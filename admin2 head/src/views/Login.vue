<template>
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="6"
            sm="8"
            md="4"
          >
          <v-layout  row justify-center>
            <v-flex sm12 md6>
                <v-card class="elevation-12" >
              <v-toolbar
                color="#004080"
                dark
                flat
              >
                <v-toolbar-title class="white--text">Login</v-toolbar-title>
                <div class="flex-grow-1"></div>
                <v-spacer></v-spacer>
                <v-tooltip right>
                  <template v-slot:activator="{ on }">
                      <router-link to="/register">
                            <v-btn
                            icon
                            large
                            href="https://codepen.io/johnjleider/pen/pMvGQO"
                            target="_blank"
                            v-on="on"
                            >
                            Register
                            </v-btn>
                      </router-link>
                    
                  </template>
                  <span class="white--text" >Become a member</span>
                </v-tooltip>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field
                    label="Login"
                    name="login"
                    v-model="username"
                    :rules="[() => !!username || 'This field is required']"
                    prepend-icon="person"
                    type="text"
                  ></v-text-field>

                  <v-text-field
                    ref="password"
                  v-model="password"
                  :rules="[() => !!password || 'This field is required']"
                  :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                  :type="showPassword ? 'text' : 'password'"
                  prepend-icon="mdi-lock"
                  label="Password"
                  placeholder="*********"
                  counter
                  required
                  @keydown.enter="login"
                  @click:append="showPassword = !showPassword"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <div class="flex-grow-1"></div>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click="login">Login</v-btn>
              </v-card-actions>
               <v-snackbar
              v-model="snackbar"
              :color="color"
              :top='true'
            >
              {{ errorMessages }}
              <v-btn
                dark
                flat
                @click="snackbar = false"
              >
                Close
              </v-btn>
            </v-snackbar>
            </v-card>

            </v-flex>
          </v-layout>
            
          </v-col>
        </v-row>
</template>

<script>
import axios from 'axios'
  export default {
    props: {
      source: String,
    },
    data: function(){
      return{
        drawer: null,
        username:'',
        password:'',
        snackbar: false,
         color: 'general',
          errorMessages: 'Incorrect login info',
          showPassword: false
      }
      
    },
    methods: {
    login: function () {
      let username = this.username
      let password = this.password
      this.$store.dispatch('login', { username, password })
        .then(() => this.$router.push('/dashboard'))
        .catch(err => {
        console.log(err)
        this.snackbar= true
        }
        )
    }
  }
  }
</script>