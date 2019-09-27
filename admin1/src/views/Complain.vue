<template>
<div class="dashboard">
    <navbar/>
    <v-layout wrap >
    <h2 class="purple--text">{{complaint}}</h2>
         <v-flex xs12 md12>
            <v-card flat class="white "  >
              <v-container fluid >
              <v-flex xs12 md6>
                  <v-text-field v-model="district"   label="District code" required ></v-text-field>
              </v-flex>
                <v-flex xs12 md6>
                  <v-text-field v-model="town"  label="Town" required ></v-text-field>
              </v-flex>
              <v-flex xs12 md12>
                  <v-select
                      v-model="select"
                      :items="itemz"
                      label="Position"
                      required
                    ></v-select>
              </v-flex>
              
                <v-flex xs12 md12>
                  <v-select
                  v-model="select2"
                  :items="items"
                  label="Classification"
                   required
                    ></v-select>
              </v-flex>
                <v-flex xs12 md12>
                  
                  <v-textarea
                    v-model="complaints"
                    counter
                    label="Complaint"
                    :rules="rules"
                    
                  ></v-textarea>
              </v-flex>
            </v-container>
            <router-link to="/team">
                <v-btn flat class="green" @click="submit()" >Submit</v-btn>
            </router-link>
            </v-card>
         </v-flex>
       </v-layout>
  
</div>
</template>

<script>
import navbar from '../components/DashViews/NavBar'
import axios from 'axios'
export default{
    components:{
      navbar
    },
  data(){
    return{
        district:'',
        town:'',
        select:'',
        select2:'',
        complaints:'',
        rules: [v => v.length <= 500 || 'Max 500 characters'],
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ],
      itemz:[
        'Staff',
        'Non Staff'
      ],
       radios: 'radio-1',
      projects:[],
      dialog: false,
      complaint:'Complaint Form'
      
     
    }
   
  },
   computed: {
    pages () {
      return this.pagination.rowsPerPage ? Math.ceil(this.items.length / this.pagination.rowsPerPage) : 0
    }
  },
  

  methods: {
   
    getColor (status) {
        if (status =="Resolved" ) return 'orange'
        else if (status=="Declined") return 'red'
        else if (status=="Unresolved") return 'purple'
        else return 'green darken-2'
      },
      submit(){
        axios.post('http://127.0.0.1:5000/postadmin1Complaint',{'email':'1234','agent_staff':this.select,
     'district':this.district,'poling_station':this.town,'nature_complaint':this.select2,'complaint':this.complaint}).then(response=>{
                window.location.reload()
            })
      }
        
      },
   
   
    

  }
 



</script>
<style lang="scoped">
/* .custom-selector{
  font-size: 3em;
  
} */
</style>
