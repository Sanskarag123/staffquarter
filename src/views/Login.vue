<template><div class="login">   
        <h1 v-if="login" v-bind="san"  >you are successfull login {{san}} </h1>
       
       
        <v-app id="inspire" v-if="!login">
    <v-content>
      <br><br><br><br>
      <v-container fluid fill-height>
        <v-layout  justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar color="primary">
                <v-toolbar-title>Login form</v-toolbar-title>
                <v-spacer></v-spacer>
                
                  
               
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field  name="login" label="Login" type="text" v-model="userdata.email"></v-text-field>
                  
                  <v-text-field  name="password" label="Password" id="password" type="password" v-model="userdata.password"></v-text-field>
     
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn  color="primary" @click="trans()" >Login</v-btn>
              </v-card-actions>
            </v-card>
            
            
          </v-flex>
        </v-layout>
                   
      </v-container>
    </v-content>
  </v-app>
  
          
          </div>
    
</template>
<script>

import router from 'vue-router';



export default { 
name:'login',
components:{


},
props:['san'],
data()
{
    return{
        user:null,
        pass:null,
        login:false,
        npass:null,
        nuser:null,
        userdata:{'email':"",'password':""
          
        }
        
        



    }
},
    
    methods:   
   { trans:function()
    { 
   
      
     
    
       if(this.userdata.email && this.userdata.password)
    { 
        this.$emit("datam",this.userdata.email);
        
       router.push({name:'home', path: "'/'" });
        this.login=true;
    
    }
    
      
        
    }
    
    
       
        
   }

    
}
 
</script>
<style scoped>

</style>


