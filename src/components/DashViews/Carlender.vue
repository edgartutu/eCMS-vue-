<template>
<div >
 
   <v-container max-height="400px" style="overflow-y: auto">
     <v-card  flat class="white"  v-for="project in projects" :key="project.content">
       <v-layout row wrap :class="`pa-3 project ${project.status}`">
         <v-flex xs12 md6>
           <div class="caption grey--text">Complaint Category</div>
           <div>{{project.content}}</div>  
         </v-flex>
         <v-flex xs4  md6>
          <div class="right">
            <v-chip  small :class="`${project.status} white--text caption my-3`">
              {{project.status}}
            </v-chip>
          </div>
         </v-flex>
       </v-layout>
        
     </v-card>
     
  </v-container>
</div>
 
</template>

<script>

export default{
  data(){
    return{
      projects:[
        {status:'pending',content:'miss use of property'},
        {status:'Resolved',content:'miss use of property'},
        {status:'pending',content:'miss use of property' },
        {status:'Declined',content:'miss use of property'}      ]

      
    }
  },

  

}

</script>

<style lang="stylus" scoped>
.project.pending{
  border-left: 4px solid #3cd1c2;
}
.project.Resolved{
  border-left: 4px solid orange;
}
.project.Declined{
  border-left: 4px solid tomato;
}
.v-chip.pending{
  background: green;
}
.v-chip.Resolved{
  background:  orange;
}
.v-chip.Declined{
  background:  tomato;
}
.v-chip{
    background:hotpink;
}

</style>
