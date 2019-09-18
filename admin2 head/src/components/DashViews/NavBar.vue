<template>
    <nav>
       <v-toolbar style=" background-color: #004080;" app fixed>
           <v-toolbar-title class="purple--text" >eCMS</v-toolbar-title>
           <p></p>
           <p></p>
            <v-toolbar-items class="hidden-sm-and-down" >
                <v-layout  row >
                <v-btn  flat small  class=" mx-2 white--text" v-for="link in links" :key="link.text" router :to="link.route">
                    <span>{{link.text}}</span>
                </v-btn>
                </v-layout>
            </v-toolbar-items>
            <v-spacer></v-spacer>
                <p></p>
                 <v-menu class="hidden-md-and-up">
                    <v-toolbar-side-icon slot="activator" class="purple--text"   ></v-toolbar-side-icon>
                    <v-list>
                    <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
                        <v-list-tile-content>
                        <v-list-tile-title class="purple--text">{{ link.text}}</v-list-tile-title>
                        </v-list-tile-content>
                    </v-list-tile>   
                    </v-list>
                </v-menu>
                <router-link v-ripple  to="/dashboard">
					<v-icon class="mx-2" color>mdi-home</v-icon><br>
				</router-link>
                <v-menu bottom left content-class offset-y transition="slide-y-transition">
					<router-link v-ripple slot="activator"  to="/projects">
						<v-badge class="#E65100" overlap>
					        <template slot="badge">{{projects.length}}</template>
					            <v-icon class="mx-2" color>mdi-bell</v-icon>
				        </v-badge>
					</router-link>
					<v-card>
						<!-- <v-list dense>
							<v-list-tile v-for="notification in notifications" :key="notification" @click="onClick">
								<v-list-tile-title v-text="notification"/>
							</v-list-tile>
						</v-list> -->
					</v-card>
				</v-menu>
                     <v-btn flat class="white--text">
                    <span>SignOut</span>
                    <v-icon>exit_to_app</v-icon>
                    </v-btn> 
        </v-toolbar>
    </nav>
</template>
<script>
export default {
    data(){
        return{
            links:[
                { text:'Dashboard', route:'/dashboard'},
                { text:'Complaints', route:'/projects'},
                { text:'Registry',route:'/team'},
                 { text:'Admistration',route:'/time'},
            ],
            projects:[
        {title:'Ec-2342-2019-041',person:'Walugembe John',due:'9/feb/2019',status:'pending',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Clone a new web',person:'jack',due:'6/march/2019',status:'Resolved',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Art a new web',person:'shot',due:'4/april/2019',status:'pending',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'},
        {title:'Keep a new web',person:'dave',due:'5/Nov/2019',status:'Declined',content:'miss use of property',
        phone:'0700418430',complaint:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Excepturi officiis, tempora suscipit amet ullam eligendi repellendus quaerat quasi quam aperiam, ut architecto veritatis. Provident, aliquid similique placeat ullam sit quod?',
        level:"Staff",Location:'Hoima',post:'supervisor',picture:'zzzzzzz'}
      ],
        }
    }
}
</script>

