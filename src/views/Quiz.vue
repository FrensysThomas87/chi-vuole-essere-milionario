<template>
   <div>
      <Domande v-for="(question, i) in quizGame[generateRandom()].domande" 
      :question = "question" 
      :key = "i"/>

      <Risposte v-for="(answer, i) in quizGame[generateRandom()].risposte" 
      :answer = "answer" 
      :key = "i"/>
   </div>
</template>


<script>
// @ is an alias to /src
import Domande from "@/components/Domande.vue";
import Risposte from "@/components/Risposte.vue";

export default {
  name: "Quiz",
  components: {
    Domande,
    Risposte,
  },

  data:function(){
     return{
            quizGame:[

            // Prima domanda
            {
               domande: [
            {
                  domanda:'Come mi chiamo?',
               }
            ],

               risposte:[
                  {
                     risposta:'Francesco',
                     bool:true,
                  },

                  {
                     risposta:'Mario',
                     bool:false,
                  },
               ]
            },

            // Seconda domanda
            {
               domande: [
             {
                  domanda:'Quanti anni ho?',
               }
            ],

               risposte:[
                  {
                     risposta:'34',
                     bool:true,
                  },

                  {
                     risposta:'40',
                     bool:false,
                  },
               ]
            },
            


        
            
      ],

      activeIndex:0,
      activeIndexAnswers:0,
      

      
    }
   },

   methods:{
      generateRandom:function(activeIndex, activeIndexAnswers){
         activeIndex = Math.floor(Math.random() * (this.quizGame.length - 1 + 1 - 0) + 0);
         activeIndexAnswers = activeIndex;
         return activeIndexAnswers;
        
         
         
      }
   }
}
</script>