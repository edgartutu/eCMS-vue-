<template>
  <div class="small" >
    <pie-chart :data="chartData" :options="chartOptions" width="100%" height="90px" ></pie-chart>
    
  </div>
</template>

<script>
import PieChart from "../PieChart.js";
import VueCharts from 'vue-chartjs'
import axios from 'axios'
export default {
  name: "App",
  components: {
    PieChart
  },
  data() {
    return {
      token: localStorage.getItem('token'),
      stuff:null,
      chartOptions: {
      hoverBorderWidth:0,
      borderWidth: "1000px",
      hoverBackgroundColor: "red",
      hoverBorderWidth: "5px",
      cutoutPercentage:0,
        
      },
      chartData: {
        hoverBackgroundColor: "red",
        hoverBorderWidth: 10,
        
        labels: ["Resolved", "Unresolved", "Pending"],
        datasets: [
          {
            label: "Data One",
            backgroundColor: ["#004080", "#E65100", "#0acfbe"],
            data:this.stuff
          }
        ]
      }
    };
  },
  created(){
    axios.post('http://127.0.0.1:5000/adminpiechart',{headers:{'x-access-token':this.token}}).then(response =>{
     
      let result= response.data.data
      this.stuff=result
      console.log(this.stuff)

    })
  },
  watch:{
    stuff(newData){
      const data =this.chartData
      data.datasets[0].data=newData
      this.chartData={...data}
    }
  },

};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
 .small {
    max-width: 400px;
    margin:  auto auto;
  }
</style>
