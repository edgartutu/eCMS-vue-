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
           
            <v-card class="elevation-12" style="margin-left:20%;margin-right:20%;">
              <v-toolbar
                color="#004080"
                dark
                flat
              >
                <v-toolbar-title class="white--text">Register form</v-toolbar-title>
                <div class="flex-grow-4"></div>
               <h2 style="margin-left:30%;" class="purple--text">eCMS</h2>
                <v-spacer></v-spacer>
                <v-tooltip right>
                  <template v-slot:activator="{ on }">
                      <router-link to="/login">
                            <v-btn
                            icon
                            large
                            href="https://codepen.io/johnjleider/pen/pMvGQO"
                            target="_blank"
                            v-on="on"
                            >
                            Login
                            </v-btn>
                      </router-link>
                  </template>
                  <span class="white--text" >Login Now</span>
                </v-tooltip>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field
                    label="Name"
                    name="login"
                    prepend-icon="person"
                    type="text"
                  ></v-text-field>

                  <v-text-field
                    label="Email"
                    name="login"
                    prepend-icon="email"
                    type="text"
                  ></v-text-field>
                  <v-text-field
                    label="Tel"
                    name="login"
                    prepend-icon="email"
                    type="text"
                  ></v-text-field>
                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    prepend-icon="lock"
                    type="password"
                  ></v-text-field>
                  <v-text-field
                    id="password"
                    label="Confirm Password"
                    name="password"
                    prepend-icon="lock"
                    type="password"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <div class="flex-grow-1"></div>
                <v-btn color="primary">Register</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
</template>
<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
    }),
  }
</script>