<template>
  <div>
    <navbar/>
  <v-layout row wrap column>       
    <v-flex xs12 md12 >
      <export-excel style="float:left;" :data="items">
            <h6  >Export to Excel</h6>
            <img src="@/assets/img/512.png" style="width:40px;height:40px">
        </export-excel>  
        <v-flex>
          <router-link to="/reports">
              <v-btn style="float:right;" ripple outlined color="indigo">Register Complaint</v-btn>
          </router-link>
        </v-flex>
      <v-text-field
            v-model="search"
            append-icon="search"
            label="Search"
            single-line
            hide-details
          ></v-text-field>
        <v-data-table class="fb-table-elem"
            :headers="headers"
            :items="items"
            :search="search"
            hide-actions
            item-key="name"
            expand >
            <template slot="items" slot-scope="props" >          
              <tr @click="props.expanded = !props.expanded">  
                <td class="datatable-cell-wrapper"><div>{{ props.item.nature_complaint }}</div></td>
                <td class="datatable-cell-wrapper"><div>{{ props.item.complaints_refn0}}</div></td>
                <td class="datatable-cell-wrapper">{{ props.item.district }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.date }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.date_submit }}</td>
                <td>
          <div class="right">
            <v-chip  small :class="`${props.item.status}  white--text caption my-2`">
              {{props.item.status}}
            </v-chip>
          </div>
         </td>
                
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
                                         <h4 class="font-weight-bold">Resolution Details</h4>
                                      <p>{{props.item.district_resolutions}}</p>
                                      
                                      
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
        search: '',
      headers: [
        { text: 'Complaint Category', value: '' },
        { text: 'Complaint Ref', value: 'complaint_refn0' },

          { text: 'Location', value: 'complaint' },
          { text: 'Date Recieved', value: 'district' },
          { text: 'Date Resolved ', value: 'date' },
           { text: 'Status ', value: 'date_submit' },
      
      ],
      items: []
      
    }
    
    },
    created(){
      axios.get('http://127.0.0.1:5000/alladmincomplaints').then(
        response =>{
          this.items = response.data
        }
      )
    }
  }
</script>
<style lang="stylus" scoped>
.item.props.Pending{
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
.v-chip.Pending{
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

