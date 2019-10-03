<template>
<div class="dashboard">
  <navbar/>
 
   <v-layout row wrap justify-space-around>
     <v-flex xs10 md5>
       <v-hover v-slot:default="{ hover }">
      <v-card :elevation="hover ? 12 : 2" class="pa-3" outline  max-width="800" height="400px">
         <pie/>
       </v-card>
       </v-hover>
     </v-flex>
     <v-flex xs10 md5>
       <v-hover v-slot:default="{ hover }">
        <v-card :elevation="hover ? 12 : 2" class="pa-2" outline max-width="800"  height="400px"> 
         <div width="1000px"><bar/></div>
         
       </v-card>
       </v-hover >
      
     </v-flex>
   </v-layout><br>
   <v-layout row wrap justify-space-around>
     <v-flex xs10 md5>
       <v-hover v-slot:default="{ hover }">
            <v-card :elevation="hover ? 12 : 2" class="pa-3" outline max-width="800"  height="400px">
         <clock/>
       </v-card>
       </v-hover>
       
     </v-flex>
     <v-flex xs10 md5 >
       <v-card max-height="400px" style="overflow-y: auto" class="pa-3" outline max-width="800"  height="400px">
         <carlender/>
       </v-card>
     </v-flex>
   </v-layout>
   

 
</div>
 
</template>

<script>
import axios from 'axios'
import pie from '../components/DashViews/PieChart.vue'
import donut from '../components/DashViews/Donut.vue';
import bar from '../components/DashViews/BarChart.vue'
import carlender from '../components/DashViews/Carlender.vue'
import navbar from '../components/DashViews/NavBar'
import clock from '../components/DashViews/Clock'

export default{
    components:{
      pie,
      donut,
      bar,
      carlender,
      navbar,
      clock
    },
  data(){
    return{
     
      
    }
  },

}

</script>