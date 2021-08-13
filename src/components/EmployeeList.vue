<template>
        <div>
                <h1> Employee List </h1>
                <table id="t01">
                        <tr>
                                <th>Name</th>
                                <th>Salary</th>
                                <th>Age</th>
                        </tr>
                         <tr v-for="item in list" v-bind:key="item.id">
                                <th>{{item.employee_name}}</th>
                                <th>{{item.employee_salary}}</th>
                                <th>{{item.employee_age}}</th>
                        </tr>
                </table>
        </div>
</template>

<script>
import Vue from 'vue';
import VueAxios from 'vue-axios'; 
import axios from 'axios';
Vue.use(VueAxios,axios)
export default {
        name:"EmployeeList",
        data() 
        {
                return {
                        list:undefined
                }
        },
        mounted()
        {
                Vue.axios.get('http://dummy.restapiexample.com/api/v1/employees')
                .then(resp=>{
                        this.list=resp.data.data
                        console.warn(resp.data.data)
                })
        }
        
}
</script>
<style scoped>
table{
        width:100%;
}
table, th, td{
        border: 1px solid black;
        border-collapse: collapse;
}
th, td{
        padding: 15px;
        text-align: left;
}
#t01 tr:nth-child(even) {
  background-color: #eee;
}
#t01 tr:nth-child(odd) {
 background-color: #fff;
}

</style>
