<template>
         <div>
            <header>
               <div id="logo-container">
                  <img src="../assets/logo_gioco.png" alt="">
               </div>
            </header>
            
            <main>
               <div class="container">
                  <Domande v-for="(question, i) in quizGame[generateRandom()].domande" 
                  :question = "question" 
                  :key = "i"/>

            <div class="answers-container">
               <Risposte v-for="(answer, i) in quizGame[generateRandom()].risposte" 
               :answer = "answer" 
               :key = "i"/>
            </div>
         </div>
      </main>
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
                  domanda:'In che anno fù fondata Roma?',
            }
         ],

               risposte:[
                  {
                     risposta:'A:1000 A.C',
                     bool:false,
                  },

                  {
                     risposta:'B:1500 A.C',
                     bool:false,
                  },

                   {
                     risposta:'C:900 A.C',
                     bool:false,
                  },

                   {
                     risposta:'D:700 A.C',
                     bool:true,
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
     
      

      
    }
   },

   methods:{
      generateRandom:function(){
         this.activeIndex = Math.floor(Math.random() * (this.quizGame.length - 1 + 1 - 0) + 0);
         console.log(this.activeIndex);
         return this.activeIndex;
      },

     
   }
}
</script>

<style lang="scss">
   
   *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      }

   header{
      background-color: #121084;
      height: 400px;
      display: flex;
      align-items: center;
      justify-content: center;

      #logo-container{
         width: 300px;
         
         img{
            width: 100%;
         }
      }
   }

   main{
      height: calc(100vh - 400px);
      background-color: #11093A;
      

      .container{
         padding-top: 15px;
         width: 1200px;
         margin: 0 auto;
         
         

          .answers-container{
             width: 100%;
            margin: 0 auto;
      }
   }

     
      
   }
</style>