<template>
<v-app>
    <div class="cont">
    <div><br>
    <v-icon >message</v-icon></div><div><br><p>Electricity bil </p></div><div><br>{{ebill}}</div>
    <div><v-btn color="primary" @click="bill()" v-if="!pay">{{status}}</v-btn><v-btn color="primary" @click="bill()" v-if="pay" disabled>{{status}}</v-btn></div></div>
    
        
    
    
    
</v-app>
    
</template>
<script>
export default {
    name:'services',
    data()
    {
        return{
            props:[{}],
            ebill:500,
            status:"pay",
            pay:null

        }
    },
        methods: {
            bill:function () {
                this.ebill=0;
                this.status="paid";
                this.pay=true;
                
            }
            
        }
    }
    

</script>
<style  scoped>
.cont
{
 float:left;

 display: grid;
 grid-template-columns: 25px auto auto auto;
 margin-top:20px; 
}

</style>



