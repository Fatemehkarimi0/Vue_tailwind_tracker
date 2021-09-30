<template>
<select
 @change="onchange()"
 v-model="Selected"
 class="form-select mt-10 block w-full border p-3 rounded">
    <option value='0'>Select Country </option>
    <option v-for="country in countries" :value='country.ID'> {{country.Country}} </option>
    </select>
</template>

<script>
export default {
    name: 'CountrySelect',
    props:['countries'],
    data(){
        return{
            selected: 0,
        }
    },
    methods:{
        onchange(){
            const country = this.countries.find((item) => item.ID === this.selected)
            console.log(country);
            this.$emit('get-country',country)
        },
    }
}
</script>