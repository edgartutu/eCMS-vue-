<template>
  <div>
    <navbar/>
  <v-layout row wrap column>       
    <v-flex xs12 md12 >
        <v-data-table class="fb-table-elem"
            :headers="headers"
            :items="items"
            hide-actions
            item-key="name"
            expand >
            <template slot="items" slot-scope="props" >          
              <tr @click="props.expanded = !props.expanded">  
                <td class="datatable-cell-wrapper"><div>{{ props.item.classify_complaint }}</div></td>
                <td class="datatable-cell-wrapper"><div>{{ props.item.complaints_refn0}}</div></td>
                <td class="datatable-cell-wrapper">{{ props.item.nature_complaint }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.district }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.date }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.date_submit }}</td>
                
                <v-dialog
                v-model="dialog"
                width="600"
                >
                  <template v-slot:activator="{ on }">
                    <v-btn
                      small 
                      class="pink"
                      v-on="on"
                    >
                    review
                    </v-btn>
                      </template>
                        <v-card>
                            <v-card-title
                            class="purple"
                          primary-title
                          style="color:white;"
                            >
                            Complaint Details
                          </v-card-title>
                                  <v-card-text class="px-16">
                                      <h4 class="font-weight-bold">Complaint Ref</h4>
                                      <p>{{props.item.complaints_refn0}}</p>
                                      <h4 class="font-weight-bold">Complaint Category</h4>
                                      <p>{{props.item.nature_complaint}}</p>
                                      <h4 class="font-weight-bold">Complainant</h4>
                                      <p>{{props.item.complaint}}</p>
                                      <h4 class="font-weight-bold">Location</h4>
                                      <p>{{props.item.district}}</p>
                                      <h4 class="font-weight-bold">Date Recieved</h4>
                                      <p>{{props.item.date}}</p>
                                        <h4 class="font-weight-bold">Date Resolved</h4>
                                      <p>{{props.item.date_submit}}</p> 
                                  </v-card-text>     
                            <v-divider></v-divider>
                            <v-card-actions>
                              <!-- <v-spacer></v-spacer> -->
                                <v-dialog
                                v-model="dialog"
                                width="200"
                                >
                                  <v-card>
                                    <v-card-text>
                                      <h4 style="color:green">Successfull</h4> 
                                    </v-card-text>
                                    <v-card-actions>
                                      <v-spacer></v-spacer>
                                      <v-spacer></v-spacer>
                                    </v-card-actions>
                                  </v-card>
                                </v-dialog>
                                <v-spacer></v-spacer>
                                <v-dialog
                                v-model="dialog"
                                width="200"
                                >
                                  <v-card>
                                    <v-card-text>
                                      <h4 style="color:red"> Rejected!</h4>
                                      </v-card-text>
                                      <v-card-actions>
                                        <v-spacer></v-spacer>
                                        </v-card-actions>
                                        </v-card>
                                        </v-dialog>
                            </v-card-actions>
                          </v-card>
                        </v-dialog>
                </tr>
              </template>
            </v-data-table>
      </v-flex>
      </v-layout>
  </div>
</template>
<script>
import navbar from '../components/DashViews/NavBar'
import axios from 'axios'
  export default {
    components:{
      navbar
    },
    data(){
    
      return {
      headers: [
        { text: 'Complaint Category', value: 'calories' },
        { text: 'Complaint Ref', value: 'calories' },
          { text: 'Complainant', value: 'fat' },
          { text: 'Location', value: 'carbs' },
          { text: 'Date Recieved', value: 'protein' },
          { text: 'Date Resolved ', value: 'iron' },
      
      ],
      items: []
      
    }
    
    
    }, 
    created(){
      axios.get('http://127.0.0.1:5000/allcomplaints').then(
        response =>{
          this.items = response.data
        }
      )
    }
  }
</script>
