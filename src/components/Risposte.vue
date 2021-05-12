<template>
<div>
  
    <div class="answers">
      <span>{{answer.risposta}}</span>
    </div>

    
     
</div>
</template>

<script>
export default {
  name: "Risposte",
  props:{
    answer: Object,
  }
  
 }
</script>

<style scoped lang="scss">

.answers{
  width:41%;
  // margin-right: 100px;
  padding: 10px 100px;
  margin-left: 73px;
  float: left;
  
  border: 1px solid #fff;

 
  margin-bottom: 15px;
  text-align: center;

  
 

    span{
      color: #fff;
    }
  }


  
</style>