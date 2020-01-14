<template>
  <div class="about">
    <h4 v-if="req">your request has been succefully send</h4>
    <label v-if="req" @click="undo()" >undo request</label>
    <h2 v-if="!req" align="center">Fill the below details for quarter request</h2>

    <v-form v-if="!req">
    
    <v-flex  sm2 d-flex>
          
        <v-select
          :items="block"
          label="block"
          v-model="blockno"
        
        ></v-select>
      </v-flex>
        
          <v-flex  sm2 d-flex>
          
        <v-select
          :items="list1"
          label="quarter no."
          v-model="flatno"
        ></v-select>
      </v-flex>
      <v-btn dark  value="request" @click="save()">request</v-btn>
      
          
        

        </v-form>
         
  </div>
</template>
<script>
export default {
  name:'about',
  data()
  {
    return{
      list:[0],
      list1:[101,102,103],
      list2:[201,202,203],
      
      flatno:null,
      blockno:null,
      block:['A','B','C'],
      req:false,
      blc:null,
      flc:null
    }
  },
  methods:
  {
    blockchange:function()
    {
      if(this.blockno=='A')
    {
      this.list=this.list1;
    }
    if(this.blockno=='B')
    {
      this.list=this.list2;
    }
    },
    save:function()
    { 
    
      this.$emit('block',this.blockno);
      this.$emit('quarter',this.flatno);
    
      this.req=true;
    
      
      
      

    },
    undo:function()
    {this.$emit('block',null);

      this.$emit('quarter',null);
      this.req=false;
      

    }
   
}
}
</script>
<style scoped>
.about
{
  padding-left: 20px;
}
label:hover{
  color:blue;
}
</style>


