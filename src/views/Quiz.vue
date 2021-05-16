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
                  :key = "i"
                  />

            
               <Risposte v-for="(answer, i) in quizGame[generateRandom()].risposte" 
               :answer = "answer" 
               :key = "i"
               :class="answer.bgColor"
               class="answers"
               v-on:catch-index="getIndex(answer)"/>
           
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
                     bgColor: ''
                  },

                  {
                     risposta:'B:1500 A.C',
                     bool:false,
                     bgColor: ''
                  },

                   {
                     risposta:'C:900 A.C',
                     bool:false,
                     bgColor: ''
                  },

                   {
                     risposta:'D:700 A.C',
                     bool:true,
                     bgColor: ''
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
                     bgColor: ''
                  },

                  {
                     risposta:'40',
                     bool:false,
                     bgColor: ''
                  },
               ]
            },
            
],

      activeIndex:0,
      answer : 'answers',
      
      activeButton:0,
    }
   },

   methods:{
      generateRandom:function(){
         this.activeIndex = Math.floor(Math.random() * (this.quizGame.length - 1 + 1 - 0) + 0);
         return this.activeIndex;
      },

      getIndex:function(array){
         
         if(array.bool === true){
            array.bgColor = 'bg-green';
         }else{
           array.bgColor = 'bg-red';
         }
      },

     

  
      
   },



  
}
</script>

<style lang="scss">
   
   *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      }

   .bg-green{
      background-color: green;
   }

   .bg-red{
      background-color: red;
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
        
         

         p{
            width: 50%;
            color: #fff;
            margin-bottom: 55px;
            padding: 10px;
            border: 1px solid #fff;
            border-radius: 20px;
            text-align: center;
            margin-left: 25%;

         
         }
         
         

            .answers{
               width:41%;
               padding: 10px 100px;
               margin-left: 73px;
               float: left;
               border: 1px solid #fff;
               border-radius: 20px;
               margin-bottom: 15px;
               text-align: center;
               cursor: pointer;

               span{
                  color: #fff;
               }
      }
   
}
     
      
   }
</style>