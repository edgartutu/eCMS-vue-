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
      stuff:{},
      chartOptions: {
        hoverBorderWidth: 10,
        
      },
      chartData: {
        hoverBackgroundColor: "red",
        hoverBorderWidth: 10,
        
        labels: ["Resolved", "Unresolved", "Pending"],
        datasets: [
          {
            label: "Data One",
            backgroundColor: ["#E65100", "#004080", "#0acfbe"],
            data:this.stuff[0].value
          }
        ]
      }
    };
  },
  created(){
    axios.post('http://127.0.0.1:5000/piechart',{'district_n0':'123432'}).then(response =>{
      //console.log(response);
      this.stuff= response.data


      
      console.log(this.stuff)

    })
  }
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
