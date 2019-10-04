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
          <v-layout row justify-center>
            <v-flex sm12 md6 >
                   <v-card class="elevation-12" >
              <v-toolbar
                color="#5e0c1d"
                dark
                flat
              >
                <v-toolbar-title class="white--text">Login form</v-toolbar-title>
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
                    prepend-icon="person"
                     :rules="[() => !!password || 'This field is required']"
                    type="text"
                  ></v-text-field>

                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    prepend-icon="lock"
                    type="password"
                     :rules="[() => !!password || 'This field is required']"
                    v-model="password"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <div class="flex-grow-1"></div>
                <v-btn color="primary" @click="login()">Login</v-btn>
              </v-card-actions>
            </v-card>
            </v-flex>
          </v-layout>
           
          </v-col>
        </v-row>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: function () {
      //drawer: null,
      return {
        username:'',
        password:'',
        drawer: null,
        
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
        //.then(response =>{console.log(response)})
        }
        )
    }
  },
  }
</script>