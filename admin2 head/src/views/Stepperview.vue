<template>
<div>
  <navbar/>
  <v-stepper v-model="e1">
    <v-stepper-header class="purple" >
      <v-stepper-step class="white--text"  :complete="e1 > 1" step="1">Complaint Details</v-stepper-step>
      <v-divider></v-divider>
      <v-stepper-step :complete="e1 > 2" step="2">Complaint Resolution</v-stepper-step>
      <v-divider></v-divider>
      <v-stepper-step step="3">View</v-stepper-step>
    </v-stepper-header>
    <v-stepper-items>
      <v-stepper-content  step="1">
        <v-container>
          <v-layout  >
            <v-flex
              xs12
              md12  
            >
            <v-card
          class="mb-12"
          flat
          >
          <v-container>
              <v-layout row wrap>
                  <v-flex xs12 md4>
                        <div class=" green--text">Complainant</div>
                        <p>{{userData.agentname}}</p>
                  </v-flex>
                  <v-flex xs12 md2>
                        <div class=" green--text">Level</div>
                        <p>{{userData.post}}</p>
                  </v-flex>
                   <v-flex xs12 md2>
                       <div class=" green--text">Position Held</div>
                         <p>{{userData.post}}</p>
                  </v-flex>
                  <v-flex xs12 md2>
                        <div class=" green--text">Phone Number</div>
                        <p>{{userData.phoneno}}</p>
                  </v-flex>
                  <v-flex xs12 md2>
                         <div class=" green--text">Location</div>
                         <p>{{userData.location}}</p>
                  </v-flex>
              </v-layout >
                <div class="red--text">Ref Number</div>
               <p>{{userData.refnumber}}</p>
                <div class=" green--text">Complaint Category</div>
               <p>{{userData.complaint}}</p>
                <div class=" green--text">Complaint Details</div>
               <p>{{userData.complaint_detail}}</p>
               
                <div class="green--text">Date</div>
               <p>{{userData.date}}</p>
                <div class=" pink--text">Level one submission</div>
               <p>...{{userData.description}}</p>
                <div class=" pink--text">Submission date</div>
               <p>...{{userData.time}}</p>
               </v-container>
               </v-card>
            </v-flex>
          </v-layout>
        </v-container>
         <decline/>
        <v-btn
        class="right"
          color="primary"
          @click="e1 = 2"
          small
          tile 
          outlined
        >
          Continue
        </v-btn>
      </v-stepper-content>

      <v-stepper-content step="2">
       
        <v-container>
          <v-layout  >
            <v-flex
              xs12
              md12  
            >
            <v-card
          class="mb-12"
          flat
          >
          <v-container>
              <v-layout row wrap>
                  <v-flex xs12 md6>
                        <v-text-field :rules="nameRules"  label="Resolver Post" required v-model="post"></v-text-field>
                  </v-flex>
                  <v-flex xs12 md6>
                        <v-text-field :rules="nameRules"  label="NiN Number" required v-model="nin"></v-text-field>
                  </v-flex>
                  <v-flex xs12 md12>
                        <v-text-field :rules="nameRules"  label="Complaint Clasification" required v-model="classification"></v-text-field>
                  </v-flex>
                  <v-flex xs12 md12>
                        <v-textarea :rules="nameRules" label="Complaint Resolution" required v-model="resolution"></v-textarea>
                  </v-flex>
                  <v-flex xs12 md12>
                        <v-textarea :rules="nameRules" label="Resolution Details" required v-model="details"></v-textarea>
                  </v-flex>
                  <v-flex xs6 md6>
                         <v-col cols="12" sm="6">
                            <v-text-field label="Signatue" single-line outlined :rules="nameRules" required v-model="signature"></v-text-field>
                        </v-col>
                  </v-flex>
                 
              </v-layout >
               </v-container>
               </v-card>
            </v-flex>
          </v-layout>
        </v-container>
        <v-btn
          class="left"
          color="primary"
          @click="e1 = 1"
          small
          tile 
          outlined
        >
          Back
        </v-btn>
        <v-btn
         :disabled="clickable"
          color="green darken-4"
          @click="e1 = 3; submit()"
        >
          Submit
        </v-btn>
        
        <v-btn class="right"
          color="primary"
          @click="e1 = 3; "
          small
          tile 
          outlined
        >
          Continue
        </v-btn>

      </v-stepper-content>
        
      <v-stepper-content step="3">
        <v-container>
          <v-layout>
            <v-flex xs12 md12>
                    <v-card  class="mb-12"  flat >
                       <v-avatar size="100">
                        <img
                            src="@/assets/img/com.jpg"
                            alt="John"
                            
                        >
                        </v-avatar>
                        <h3>Orgainsation Name</h3>
                        <h3 style="color: #004080;" class="font-weight-bold">Certificate Of Resolution</h3>
                        <h4 class="red--text" style="font-weight:bold;">{{userData.refnumber}}</h4>
                        <h4 class="font-weight-bold">Complaint</h4>
                        <p>{{userData.complaint_detail}}</p>
                        <h4 class="font-weight-bold" >HeadQuater Resolution :</h4>
                        <p>{{userData.resolving}}</p>
                        <div class="left " >ReportDate:  {{userData.date}}  </div><br>
                        <div class="left">ResolvedDate: {{userData.dt}}</div>
                        <div class="right">signature: ...........................................</div>
                        <br>
                        <div class="right">Director Technical And Support Services</div>
                        
                        <!-- <p class="left"> </p> -->

                        
                    </v-card>
            </v-flex>
          </v-layout>
        </v-container>
         <v-btn
          class="left"
          color="primary"
          @click="e1 = 2"
          small
          tile 
          outlined
        >
          Previous
        </v-btn>
        <v-btn
        class="right"
          color="teal"
        >
          Print
        </v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
  </div>
</template>
<script>
import axios from 'axios'
import data1 from '@/views/Complaints.vue'
import decline from '../components/DashViews/Decline.vue'
  import router from '../router'
  import navbar from '../components/DashViews/NavBar'
  export default {
      name:'Stepperview',
    components:{
      data1,
      decline,
      navbar
    },
    data () {
      return {
        e1: 0,
        userData: 0,
        debug: false,
        post:"",
        nin:"",
        classification:"",
        resolution:"",
        details:"",
        signature:"",
        nameRules: [
        v => !!v || 'Input is required',
        // v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      user: localStorage.getItem('user'),
      token: localStorage.getItem('token')
      
      }
    },
    created() {
            this.userData = this.$route.params.userData;
        },
        computed: {
  isDisabled() {
    if (status =="Resolved" ){
      return false;
    }else{
      return true;
    }
    
  }
},
    methods:{
      submit(){
        axios.post('http://127.0.0.1:5000/adminpostcomplaints',{
          'status':'Resolved','complaints_refn0':this.userData.refnumber, 'admin_email':this.user,
          'nin':this.nin,'districtagent_post':this.post,
          'district_resolutions':this.resolution,'classify_complaint':this.classification,
          'district_description':this.details,
          'head_signature':this.signature
          },{headers:{'x-access-token':this.token}})
      }
    }
  }
</script>