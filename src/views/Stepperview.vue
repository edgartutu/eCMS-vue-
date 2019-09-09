<template>
  <v-stepper v-model="e1">
    <v-stepper-header >
      <v-stepper-step  :complete="e1 > 1" step="1">Complaint Details</v-stepper-step>
      <v-divider></v-divider>
      <v-stepper-step :complete="e1 > 2" step="2">Complaint Resolution</v-stepper-step>
      <v-divider></v-divider>
      <v-stepper-step step="3">View</v-stepper-step>
    </v-stepper-header>
    <v-stepper-items>
      <v-stepper-content step="1">
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
                        <p>{{userData.levels}}</p>
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
                        <v-text-field :rules="nameRules"  label="Resolver Post" required></v-text-field>
                  </v-flex>
                  <v-flex xs12 md6>
                        <v-text-field :rules="nameRules"  label="NiN Number" required></v-text-field>
                  </v-flex>
                  <v-flex xs12 md12>
                        <v-text-field :rules="nameRules"  label="Complaint Clasification" required></v-text-field>
                  </v-flex>
                  <v-flex xs12 md12>
                        <v-textarea :rules="nameRules" label="Complaint Resolution" required ></v-textarea>
                  </v-flex>
                  <v-flex xs12 md12>
                        <v-textarea :rules="nameRules" label="Resolution Details" required ></v-textarea>
                  </v-flex>
                  <v-flex xs6 md6>
                         <v-col cols="12" sm="6">
                            <v-text-field label="Signatue" single-line outlined :rules="nameRules" required ></v-text-field>
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
        >
          Back
        </v-btn>
        <v-btn
         
          color="green darken-4"
          @click="e1 = 3"
        >
          Submit
        </v-btn>
        
        <v-btn class="right"
          color="primary"
          @click="e1 = 3"
          small
        >
          Continue
        </v-btn>

      </v-stepper-content>
        
      <v-stepper-content step="3">
        <v-container>
          <v-layout>
            <v-flex xs12 md12>
                    <v-card  class="mb-12"  flat ></v-card>
            </v-flex>
          </v-layout>
        </v-container>
         <v-btn
          class="left"
          color="primary"
          @click="e1 = 2"
          small
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
</template>
<script>
import data1 from '@/views/Project.vue'
import decline from '../components/DashViews/Decline.vue'
  import router from '../router'
  export default {
      name:'Stepperview',
    components:{
      data1,
      decline,
    },
    data () {
      return {
        e1: 0,
        userData: 0,
        debug: false,
        nameRules: [
        v => !!v || 'Input is required',
        // v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      
      }
    },
    created() {
            this.userData = this.$route.params.userData;
        },
    
  }
</script>