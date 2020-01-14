<template><div id="app">
<v-app>
  
  <v-toolbar color="primary"  app>
    <img src="./assets/srm logo.png" width="30px" href="http://www.srmuniv.ac.in">
    <v-toolbar-title>Staff Quarters</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn key="'Home'" to="/" flat>home</v-btn>
      <v-btn key="'About'" to="/about" v-if="name" flat>Quarter-req</v-btn>
       <v-btn key="'About'" to="/about" v-if="!name" disabled flat>Quarter-req</v-btn>
        <v-btn key="'Services'" to="/services" v-if="name" flat>Services</v-btn>
        <v-btn key="'Services'" to="/services" v-if="!name" flat disabled>Services</v-btn>
      <v-btn  key="'Login'" to="/login" @click="status()" flat>{{log}}</v-btn>
      
    </v-toolbar-items>
  </v-toolbar>
  <v-content>
    <div class="grid-container" >
      <div class="b1" v-if="log=='logout'">
        <v-card  elevation="5" min-height="800px">
          <v-img src="./assets/web.jpeg" min-width="200px" aspect-ratio="1.7"></v-img>
          <div v-if="!logout || name"><h3>The user id is {{name}}</h3><h3 v-if="block">you have requested for block{{block}}<br>quarter no{{flatno}}</h3></div>
          <p ></p>
          <p></p>
        </v-card>
   
       
    

     
      </div>
      <div  class="b2">
         
    <router-view v-on:datam="update"  v-on:block="req1" v-on:quarter="req2"  v-bind:san="logout"/>
      </div>
        

      </div>
  
  </v-content>

</v-app>
 <v-footer app dark class="pa-3">
    <v-spacer></v-spacer><h4>srm university  </h4>
    <div>&copy; {{ new Date().getFullYear() }}</div>
  </v-footer>
          
          
          
          </div>
          
  
</template>

<script>
import Login from './views/Login.vue'
import About from './views/About.vue'
import Home from './views/Home.vue'
import Services from './views/Services.vue'
import axios from 'axios';




export default {
  name: 'app',
  components: {
    Login,About,Home
    
  },
  props:{tp:null

  },
  data () {
    return {
      name:null,
      
      log:"login",
      block:null,
      flatno:null,
      logout:true,
      userdetail:{
        name:'sanskar',
        password:"sanskar2311"
      }    //
    }
  },
  mounted() {
    axios.get('https://serverwork.herokuapp.com/api')
    .then((response)=>{
      console.log(response)
    })
    
  },
  
  methods:{
    update:function(ok1)
    {
      this.name=ok1;
      if(this.name)
      {
        this.log="logout";
      }
      
      
    },
    validate:function(name)
    {
      this.tp=name;
    },
    req1:function(intm)
    {
      this.block=intm;
    },
    req2:function(op)
    {
      this.flatno=op;
    },
    status:function()
    { 
      if(this.log=="logout")
      {
      this.log="login";
      this.logout=true;
      this.name=null
      
      }
      
    }



  }
  
}
</script>
<style scoped>
.grid-container
{
  display: flex;
  grid-template-columns: auto auto;
}
.b1{
  flex: 1;
}
.b2
{
  flex:4;
}


</style>

