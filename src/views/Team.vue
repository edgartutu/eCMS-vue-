<template>

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
                <td class="datatable-cell-wrapper"><div>{{ props.item.name }}</div></td>
                <td class="datatable-cell-wrapper"><div>{{ props.item.calories}}</div></td>
                <td class="datatable-cell-wrapper">{{ props.item.fat }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.carbs }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.protein }}</td>
                <td class="datatable-cell-wrapper">{{ props.item.iron }}</td>
                
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
                            class="headline grey lighten-2"
                          primary-title
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
                                  </v-card-text>     
                            <v-divider></v-divider>
                            <v-card-actions>
                              <v-spacer></v-spacer>
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

</template>
<script>

  export default {
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
      items: [
                {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Mugerwa steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019',
          },
          {
            name: 'Lost of material',
            calories: 'EC-2343-2019-334',
            fat: 'walugembe steven',
            carbs: 'Kampala',
            protein: '5/08/2019',
            iron: '7/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Namugerwa jane',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Mugerwa steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
           name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Kabali steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'mutawe peter',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Sejuuko paul',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Aki steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Arinaitwe John',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
          {
            name: 'Theft of material',
            calories: 'EC-2343-2019-334',
            fat: 'Opio steven',
            carbs: 'Mbale',
            protein: '2/08/2019',
            iron: '4/10/2019'
          },
       
      ]
      
    }
    
    }, 
  }
</script>
