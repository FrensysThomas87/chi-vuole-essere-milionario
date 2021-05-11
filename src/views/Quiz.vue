<template>
   <div>
      <Domanda v-for="(question, i) in quizGame" 
      :question = "question" 
      :key = "i"/>
   </div>
</template>


<script>
// @ is an alias to /src
import Domande from "@/components/Domande.vue";

export default {
  name: "Quiz",
  components: {
    Domande,
  },

  data:function(){
     return{
            quizGame:[
         {
         domanda: 'Quanti anni ho?',
         risposta: '34',
        },

        {
           domanda: 'Di dove sono?',
           risposta: 'Perugia',
        },
      ]
     }
 
   }
}
</script>