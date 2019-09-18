<template>
<div class="dashboard">
    <navbar/>
    <v-form>
      <v-container fluid>
        <v-row>
          <v-layout row wrap >
            <v-flex xs10 md3>
              <v-col cols="12" sm="4">
                <v-text-field
                  :rules="rules"
                  counter="25"
                  label="Level 1 Code"
                  outlined
                ></v-text-field>
            </v-col>
            </v-flex>
              <v-btn class="mx-2" fab dark large color="cyan">
                  Search
               </v-btn>
               <v-spacer></v-spacer>
                <v-flex xs10 md3>
              <v-col cols="12" sm="4">
                <v-text-field
                  :rules="rules"
                  counter="25"
                  label="User Code"
                  outlined
                ></v-text-field>
            </v-col>
            </v-flex>
              <v-btn class="mx-2" fab dark large color="cyan">
                  Search
               </v-btn>
          </v-layout>    
        </v-row>
      </v-container>
    </v-form>
   <v-container fluid>
     <v-layout row class="mb-2">
       <v-tooltip top>
         <v-btn small flat class="primary" @click="sortBy('title')" slot="activator">
         <v-icon left small >folder</v-icon>
         <span class="caption text-lowercase">By Complaint</span>
        </v-btn>
        <span class="white--text">sort product by Complaint</span>
       </v-tooltip>
       <v-tooltip top>
          <v-btn small flat class="primary" @click="sortBy('status')" slot="activator">
         <v-icon left small >person</v-icon>
          <span class="caption text-lowercase">By status</span>
        </v-btn>
        <span class="white--text">sort by status</span>
       </v-tooltip>

     </v-layout>
     <v-card flat class="white"  v-for="project in projects" :key="project.title">
       <v-layout row wrap :class="`pa-3 project ${project.status}`">
         <v-flex xs12 md4>
           <div class="caption grey--text">Complaint Category</div>
           <div>{{project.content}}</div>  
         </v-flex>
         <v-flex xs6 sm4 md2>
           <div class="caption grey--text">Ref Number</div>
           <div>{{project.title}}</div>
         </v-flex>
         <v-flex xs6 sm4 md2>
           <div class="caption grey--text">Agent Name</div>
           <div>{{project.person}}</div>
         </v-flex>
         <v-flex xs6 sm4 md2>
           <div class="caption grey--text">Date</div>
           <div>{{project.due}}</div>
         </v-flex>
         
         <v-flex xs2 sm4 md1>
          <div class="right">
            <v-chip  small :class="`${project.status}  white--text caption my-2`">
              {{project.status}}
            </v-chip>
          </div>
         </v-flex>
         <v-flex xs2 sm4 md1>
           <router-link   :to="{ name: 'Stepperview',
            params: { userData:{complaint:project.content,refnumber:project.title,agentname:project.person,
            date:project.due,phoneno:project.phone,location:project.Location,
            complaint_detail:project.complaint,levels:project.level,post:project.post,picto:project.picture} } }" >
				    <v-btn
                :color="getColor(project.status)"
                dark
                small
                class="mx-2"
              >
              <div class="mx-2">Reslove</div>
              </v-btn>
				</router-link>
         </v-flex>
       </v-layout>
       <v-divider></v-divider>
     </v-card>
     <!-- <div class="text-center">
    <v-pagination v-model="pagination.page" :length="pages"></v-pagination>
  </div> -->
  </v-container>
</div>
</template>

<script>
import navbar from '../components/DashViews/NavBar'
export default{
    components:{
      navbar
    },
  data(){
    return{
      
     e1: 0,
    // pagination: {
      
    // },
    
      projects:[
        {title:'Ec-2342-2019-041',person:'Walugembe John',due:'9/feb/2019',status:'pending',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Clone a new web',person:'jack',due:'6/march/2019',status:'Resolved',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Art a new web',person:'shot',due:'4/april/2019',status:'pending',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Keep a new web',person:'dave',due:'5/Nov/2019',status:'Declined',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Keep a new web',person:'dave',due:'5/Nov/2019',status:'Unresolved',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'}
      ],
      dialog: false,
      
     
    }
   
  },
   computed: {
    pages () {
      return this.pagination.rowsPerPage ? Math.ceil(this.items.length / this.pagination.rowsPerPage) : 0
    }
  },

  methods: {
    sortBy(prop){
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1:1)

    },
    getColor (status) {
        if (status =="Resolved" ) return 'orange'
        else if (status=="Declined") return 'red'
        else if (status=="Unresolved") return 'purple'
        else return 'green darken-2'
      }
        
      },
   
   
    

  }
 



</script>
<style lang="stylus" scoped>
.project.pending{
  border-left: 4px solid green
}
.project.Resolved{
  border-left: 4px solid orange
}
.project.Declined{
  border-left: 4px solid tomato
}
.project.Unresolved{
  border-left: 4px solid purple
}
.v-chip.pending{
  background: green 
}
.v-chip.Resolved{
  background:  #004080
}
.v-chip.Declined{
  background:  tomato
}
.v-chip.Unresolved{
  background:  purple
}
</style>
