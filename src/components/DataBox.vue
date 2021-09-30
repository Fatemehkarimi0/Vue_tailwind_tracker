<template>
    <div class="grid md:grid-cols-2 gap-4">
        <!--Cases Box-->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New :</span>
                {{numberformatter(state.NewConfirmed )}}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total :</span>
                {{numberformatter(state.TotalConfirmed)}}
            </div>
        </div>

        <!--Death Boxs-->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Death</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New :</span>
                {{numberformatter(state.NewDeaths)}}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total :</span>
                {{numberformatter(state.TotalDeaths)}}
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:'DataBox',
        props:['state'],
        methods:{
            numberformatter(x){
                return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g , ',')
            }
        }
    }
</script>