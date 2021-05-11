<template>
  <div>
     <p>{{question.domanda}}</p>
  </div>
</template>

<script>
export default {
  name: "Domande",
  props:{
    question: Object,
  }
  
 }
</script>

<style scoped>

</style>