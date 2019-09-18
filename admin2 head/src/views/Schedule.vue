<template>
    <div>
        <navbar/>
        <v-layout row wrap justify-space-around>
     <v-flex xs10 md5>
       <v-card class="pa-3" outline  max-width="800" height="400px">
      
       </v-card>
     </v-flex>
     <v-flex xs10 md5>
       <v-card class="pa-2" outline max-width="800"  height="400px"> 
         <div width="1000px"></div>
         
       </v-card>
     </v-flex>
   </v-layout><br>
        
    </div>
</template>
<script>
import navbar from '../components/DashViews/NavBar'
import oclock from '../components/DashViews/Oclock'
export default {
    components:{
        navbar,
        oclock
    }
}
</script>