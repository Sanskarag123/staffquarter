<template>
 <div class="home">
     <v-app>
         <h1>QUARTER ALLOTMENT AND SERVICES SYSTEM   </h1>
         <ul class="status">
             <li class="stat" >Total Quarters</li>
             <li class="stat">Allotted Quarters</li>
             <li class="stat">Vacant Quarters</li>
             <li class="stat">Quarters Under Repair</li>
         </ul> 
           
     </v-app>
 </div>
</template>
<style scoped>
h1{
    text-align: center;
}
.stat
{
    display: inline;
    font-size: 20px;
    font-style: bold;
    padding: 30px;
}
.status
{
    margin:0 auto
}
ul{
    display: flex;
    flex:center;
}

</style>

