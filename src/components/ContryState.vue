<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-6">
                <select @change="change" v-model="selectedContry" class="form-control bg-dark text-white" id="exampleFormControlSelect2">
                    <option v-for="d in data" :value="d.country" :selected="d.country=='Morocco'" :key="d.country">{{d.country}}</option>
                </select>
            </div>
        </div>
        <div class="row justify-content-center mt-3">
            <div class="col-6 text-center text-white">{{selectedContry}}</div>
        </div>

        <div class="container mt-4">
            <div class="row justify-content-center">
                <div class="col-md-6 col-12">
                    <div class="row justify-content-center">
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">الحالاة</h6>
                            <span class="d-block mt-3">{{countryCases}}</span>
                        </div>                                  
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">حالات اليوم</h6>
                            <span class="d-block mt-3">{{countryTodayCases}}</span>
                        </div>                                  
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">الوفيات</h6>
                            <span class="d-block mt-3">{{countryDeaths}}</span>
                        </div>                                  
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">وفيات اليوم</h6>
                            <span class="d-block mt-3">{{countryTodayDeaths}}</span>
                        </div>                                  
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">الحالات المعالجة</h6>
                            <span class="d-block mt-3">{{countryRecoverd}}</span>
                        </div>                                  
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">الحالاة الحرجة</h6>
                            <span class="d-block mt-3">{{countryCritical}}</span>
                        </div>                                  
                        <div class="col-3 m-1 text-center bg-dark text-white rounded item-d p-2">
                            <h6 class="mt-1">عدد الحالات لكل مليون</h6>
                            <span class="d-block mt-3">{{countryPerMill}}</span>
                        </div>                                  
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name:'ContryState',
    created(){
        axios.get('https://corona.lmao.ninja/v2/countries')
        .then(Response =>{
            this.data = Response.data;
            this.getData();
        })
        .catch(error => {
            console.log(error)
        });

        
    },
    data(){
        return{
            data:null,
            selectedContry:'Morocco',
            countryCases:0,
            countryTodayCases:0,
            countryDeaths:0,
            countryTodayDeaths:0,
            countryRecoverd:0,
            countryCritical:0,
            countryPerMill:0,
            selected:null
        }
    },
    methods:{
        change:function(e){
            this.selectedContry = e.target.value;
            this.getData();
        },
        getData: function(){
            // axios.get('https://corona.lmao.ninja/countries/'+this.selectedContry)
            // .then(Response =>{
            //     this.countryCases = Response.data.cases;
            //     this.countryTodayCases = Response.data.todayCases;
            //     this.countryDeaths = Response.data.deaths;
            //     this.countryTodayDeaths = Response.data.todayDeaths;
            //     this.countryRecoverd = Response.data.recovered;
            //     this.countryCritical = Response.data.critical;
            //     this.countryPerMill = Response.data.casesPerOneMillion;
            // })
            // .catch(error =>{
            //     console.log(error);
            // })

            // this.selected = this.data.filter(c=>{
            //     console.log(c.country);
            //     return c.country === 'Morocco';
            // })

            this.selected = this.data.filter(c => {
                return c.country == this.selectedContry;
            });

            this.countryCases = this.selected[0].cases;
            this.countryTodayCases = this.selected[0].todayCases;
            this.countryDeaths = this.selected[0].deaths;
            this.countryTodayDeaths = this.selected[0].todayDeaths;
            this.countryRecoverd = this.selected[0].recovered;
            this.countryCritical = this.selected[0].critical;
            this.countryPerMill = this.selected[0].casesPerOneMillion;
            // console.log(this.selectedContry);
        }
    }
}
</script>
<style>
    .form-control{
        border: none;
    }
    .form-control:focus,
    .form-control:active{
        outline: none;
        box-shadow: none;
        border: none;
    }
    .item-d{
        min-height: 100px;
    }
</style>