<template>
  <div>
    <navbar/>
  <v-layout row wrap column>       
    <v-flex xs12 md12 >
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
                <td class="datatable-cell-wrapper"><div>{{ props.item.name }}</div></td>
                <td class="datatable-cell-wrapper"><div>{{ props.item.calories}}</div></td>
                <td class="datatable-cell-wrapper">{{ props.item.carbs }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.protein }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.iron }}</td>
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
                                      <p>{{props.item.name}}</p>
                                      <h4 class="font-weight-bold">Complaint Category</h4>
                                      <p>{{props.item.calories}}</p>
                                      <h4 class="font-weight-bold">Complainant</h4>
                                      <p>{{props.item.fat}}</p>
                                      <h4 class="font-weight-bold">Location</h4>
                                      <p>{{props.item.carbs}}</p>
                                      <h4 class="font-weight-bold">Date Recieved</h4>
                                      <p>{{props.item.protein}}</p>
                                        <h4 class="font-weight-bold">Date Resolved</h4>
                                      <p>{{props.item.iron}}</p> 
                                         <h4 class="font-weight-bold">Resolution Details</h4>
                                      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt magnam necessitatibus adipisci, quam a quidem, alias eum amet quos aperiam provident sequi in vero voluptas ea pariatur assumenda, eos dolorum!</p> 
                                      
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
  export default {
    components:{
      navbar
    },
    data(){
    
      return {
        search: '',
      headers: [
        { text: 'Complaint Category', value: 'calories' },
        { text: 'Complaint Ref', value: 'calories' },

          { text: 'Location', value: 'carbs' },
          { text: 'Date Recieved', value: 'protein' },
          { text: 'Date Resolved ', value: 'iron' },
           { text: 'Status ', value: 'status' },
      
      ],
      items: [
                {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Mugerwa steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'pending'
          },
          {
            name: 'Lost of material',
            calories: 'EC-2343-2019-334',
            fat: 'walugembe steven',
            carbs: 'Kampala',
            protein: '5/08/2019',
            iron: '7/10/2019',
            status:'Resolved'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Namugerwa jane',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'pending'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Mugerwa steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'Declined'
          },
          {
           name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Kabali steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'Declined'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'mutawe peter',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'pending'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Sejuuko paul',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'Resolved'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Aki steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'pending'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Arinaitwe John',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'Resolved'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Opio steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
            status:'Declined'
          },
       
      ]
      
    }
    
    }, 
  }
</script>
<style lang="stylus" scoped>
.item.props.pending{
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
.v-chip.pending{
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

