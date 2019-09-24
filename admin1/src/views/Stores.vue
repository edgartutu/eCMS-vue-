<template>
  <div>
    <navbar/>
  <v-layout row wrap column>  
    <v-flex xs12 md12 >
        <export-excel :data="items">
            <h6 >Export to Excel</h6>
            <img src="@/assets/img/512.png" style="width:40px;height:40px">
        </export-excel>  
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
            <template slot="items" slot-scope="{item,index}" >          
              <!-- <tr @click="props.expanded = !props.expanded">   -->
                <td class="datatable-cell-wrapper"><div>{{ item.nature_complaint }}</div></td>
                <td class="datatable-cell-wrapper"><div>{{ item.complaints_refn0}}</div></td>
                <td class="datatable-cell-wrapper">{{ item.complaint }}</td>
                <td class="datatable-cell-wrapper">{{ item.comment }}</td>
                <td class="datatable-cell-wrapper">{{ item.date }}</td>
                <td class="datatable-cell-wrapper red--text">{{ item.status }}</td>
                <v-btn small class="lime darken-1" @click="retrieve(index)">Retrieve</v-btn>
                
                <!-- </tr> -->
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
          posts:'',
          search: '',
          status:'',
          
      headers: [
        { text: 'Complaint Category', value: 'calories' },
        { text: 'Complaint Ref', value: 'calories' },
          { text: 'Complainant', value: 'fat' },
          { text: 'Comments', value: 'carbs' },
          { text: 'Date Recieved', value: 'protein' },
          { text: 'Status ', value: 'iron' },
      
      ],
      items: [],
      complaints_refn0:''
      
    }
    
    
    }, 
    created(){
      axios.get('http://127.0.0.1:5000/AllDeclinedComplaints').then(
        response =>{
          this.items = response.data
        }
      )
    },
    methods:{
        retrieve(index){
            this.complaints_refn0 = this.items[index].complaints_refn0
             axios.post('http://127.0.0.1:5000/updatedeclinedcomplaint',{'admin_email':1234,
             'complaints_refn0':this.complaints_refn0,'status':'Pending'})
            .then(response=>{
                window.location.reload()
            })


             
             
        },
         exportdb() {
                axios.post("http://127.0.0.1:5000/excelexport1").then(response => {
                    console.log(response)
                })
            },
    }
  }
</script>
