<template>
  <div >
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          color="red"
          dark
          v-on="on"
          class="left"
        >
          Decline
        </v-btn>
      </template>

      <v-card>
        <v-card-text>
           <v-container>
              <v-layout row wrap>
                  <v-flex xs12 md12>
                        <v-textarea :rules="nameRules" label="Decline Resolution" required ></v-textarea>
                  </v-flex>

              </v-layout >
               </v-container>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <div class="flex-grow-1"></div>
          <v-btn
            color="primary"
            text
            @click="dialog = false; submit()"
          >
            Submit
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
import axios from 'axios'
  export default {
    data () {
      return {
        dialog: false,
        userData: 0,
        comment:"",
        nameRules: [
        v => !!v || 'Input is required',
        // v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      }
    },
    created() {
          this.userData = this.$route.params.userData;
        },
    method:{
      submit(){
        axios.post('http://127.0.0.1:5000/adminpostcomplaints',{
          'status':'Declined','comment':this.comment,'complaints_refn0':this.userData.refnumber, 'admin_email':1234
          })
      }
    }
  }
</script>