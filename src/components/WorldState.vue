<template>
    <div class="container">
        <div class="row justify-content-center mt-3">
            <div class="col-6 text-center text-white mb-3">الاحصائيات العالمية</div>
        </div>
        <div class="row justify-content-center">
            <WorldStateItem title="عدد الحالات" :count="cases" />
            <WorldStateItem title="الموتى" :count="deaths" />
            <WorldStateItem title="الحالات المعاجة" :count="recovered" />
        </div>
    </div>
</template>

<script>
import WorldStateItem from './WorldStateItem.vue';
import axios from 'axios';

export default {
    name:'WorldState',
    components:{
        WorldStateItem
    },
    data(){
        return{
            worldData: null,
            cases:0,
            deaths:0,
            recovered:0
        }
    }
    ,
    created(){
        axios.get('https://corona.lmao.ninja/v2/all')
        .then(Response => {
            console.log(Response.data);
            this.worldData = Response.data;
            this.cases = this.worldData.cases;
            this.deaths = this.worldData.deaths;
            this.recovered = this.worldData.recovered;
        })
        .catch(error =>{
            console.log(error);
        })
    }
}
</script>
<style>
    
</style>