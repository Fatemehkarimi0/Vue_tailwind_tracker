<template>
  <main v-if="!loading">

  <DataTitle
  :text="title"
  :dataDate="dataDate" />
  <DataBox
  :state="state" />
  <CountrySelect
  @get-country="getCountryData"
  :countries="countries" />

  </main>

  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10  mb-6">
      Fetching Data
    </div>
  </main>

</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBox from '@/components/DataBox'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBox,
    CountrySelect
  },
  data(){
 return{
   loading :true,
    title: 'Global',
    dataDate : '',
    state :{},
    countries:[],
 }
  },
  methods:{
    async  fetchcovid(){
      const res = await  fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
  },
  async created(){
    const data = await this.fetchcovid()
    console.log(data);
    this.dataDate = data.Date
    this.state = data.Global
    this.countries = data.Countries
    this.loading = false
    },
}
</script>
