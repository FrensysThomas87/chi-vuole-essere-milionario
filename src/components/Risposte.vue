<template>
<div>
  
    <div v-on:click="$emit('catch-index')">
      <span>{{answer.risposta}}</span>
    </div>

    
     
</div>
</template>

<script>

export default {
  name: "Risposte",
  props:{
    answer: Object,
  },

  data:function(){
    return{
      
    }
  },
}


  
 
</script>

<style  lang="scss">



// .answers{
//   width:41%;
//   padding: 10px 100px;
//   margin-left: 73px;
//   float: left;
//   border: 1px solid #fff;
//   border-radius: 20px;
//   margin-bottom: 15px;
//   text-align: center;
//   cursor: pointer;

  //    &:hover{
  //       background-color: #fff;

  //   }

  //   &:hover span{
  //     color:#11093A;
  //   }

 
  // span{
  //     color: #fff;
  //   }
  


  
</style>