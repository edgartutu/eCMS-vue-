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
                  <!-- <v-flex xs6 md6>
                         <v-col cols="12" sm="6">
                            <v-text-field label="Signatue" single-line outlined :rules="nameRules" required ></v-text-field>
                        </v-col>
                  </v-flex> -->
              </v-layout >
               </v-container>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <div class="flex-grow-1"></div>
          <v-btn
            color="primary"
            text
            @click="dialog = false"
          >
            Submit
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>