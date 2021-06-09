<template>
         <div>
            <header>
               <div id="logo-container">
                  <img src="../assets/logo_gioco.png" alt="">
               </div>
            </header>

               <audio autoplay>
                  <source src="../assets/bensound-epic.mp3">
               </audio>
            
            <main>
              
               <div class="container" v-if="inGame === true">

                 

                  <Domande v-for="(question, i) in quizGame[activeIndex].domande" 
                  :question = "question" 
                  :key = "i"/>

            
                  <Risposte v-for="(answer, i) in quizGame[activeIndex].risposte" 
                  :answer = "answer" 
                  :key = "i"
                  :class="answer.bgColor"
                  class="answers"
                  v-on:give-color="giveColor(answer)"
                  v-on:next-question="delayNextQuestion(answer)"/>
           
               </div>
         <h2 class="score" v-if="inGame">Il tuo patrimonio è: € {{currentAmount}}</h2>
         <!-- <h2 class="score" v-if="inGame">Il tuo punteggio attuale è: {{counterCorrect}}</h2> -->
         <h2 class="score" v-else>Il tuo punteggio finale è: {{counterCorrect}}</h2>
         <h2 id="incorrect-counter" v-if="inGame === false">Hai sbagliato {{counterFalse}} domade</h2>
         <div id="play-again" v-if="inGame === false"  @click="playAgain">Gioca ancora</div>
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
                  questioned: false
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
                     bgColor: '',
                     amount: 500
                  },
               ]
            },

            // Seconda domanda
            {
               domande: [
             {
                  domanda:'In che anno cadde l\'Impero Romano?',
                  questioned: false
               }
            ],

               risposte:[
                  {
                     risposta:'A:100 D.C',
                     bool:false,
                     bgColor: ''
                  },

                  {
                     risposta:'B:300 D.C',
                     bool:false,
                     bgColor: ''
                  },

                   {
                     risposta:'C:476 D.C',
                     bool:true,
                     bgColor: '',
                     amount: 1000
                  },

                   {
                     risposta:'D:500 D.C',
                     bool:false,
                     bgColor: ''
                  },
               ]
            },

             {
               domande: [
             {
                  domanda:'Come si chiamava il famoso generale della seconda guerra punica?',
                  questioned: false
               }
            ],

               risposte:[
                  {
                     risposta:'A:Lucio',
                     bool:false,
                     bgColor: ''
                  },

                  {
                     risposta:'B:Sannicandro',
                     bool:false,
                     bgColor: ''
                  },

                   {
                     risposta:'C:Annibale',
                     bool:true,
                     bgColor: '',
                     amount: 2000
                  },

                   {
                     risposta:'D:Mitride',
                     bool:false,
                     bgColor: ''
                  },
               ]
            },

             {
               domande: [
             {
                  domanda:'In che anno è avvenuta l\'unità d\'Italia?',
                  questioned: false
               }
            ],

               risposte:[
                  {
                     risposta:'A:1820',
                     bool:false,
                     bgColor: ''
                  },

                  {
                     risposta:'B:1861',
                     bool:true,
                     bgColor: '',
                     amount: 10000
                  },

                   {
                     risposta:'C:1848',
                     bool:false,
                     bgColor: ''
                  },

                   {
                     risposta:'D:1850',
                     bool:false,
                     bgColor: ''
                  },
               ]
            },


            {
               domande: [
            {
                  domanda:'L\'HTML è',
                  questioned: false
            }
         ],

               risposte:[
                  {
                     risposta:'Un liguaggio di programmazione',
                     bool:false,
                     bgColor: ''
                  },

                  {
                     risposta:'Un liguaggio di markup',
                     bool:true,
                     bgColor: '',
                     amount: 50000
                  },

                   {
                     risposta:'Un\'unità di misura',
                     bool:false,
                     bgColor: ''
                  },

                   {
                     risposta:'Uno standard ISO',
                     bool:false,
                     bgColor: '',
                     
                  },
               ]
            },
            
            
],

      activeIndex:0,
      usedNumbers: [],
      inGame: true,
      counterCorrect:0,
      counterFalse:0,
      spliced:0,
      arrcounterCorrect:0,
      currentAmount:0,
      
      
      
    }
   },

   methods:{
      nextQuestion:function(){
       
            //   this.activeIndex = Math.floor(Math.random() * (this.quizGame.length  + 1 - 0) + 0);


            //    if(!this.usedNumbers.includes(this.activeIndex)){
            //       this.activeIndex++;
            //       this.usedNumbers.push(this.activeIndex);
                  
            // }

            // for(var i = 0; i < this.usedNumbers.length;i++){
            //    this.activeIndex = i;
            // }

            this.activeIndex++;
            if(this.activeIndex === this.quizGame.length){
               this.inGame = false;
            }
        
         },

      playAgain:function(){
         this.activeIndex = 0;
         this.counterCorrect = 0;
         this.counterFalse = 0;
         this.inGame = true;
      },

      giveColor:function(array){
         
         if(array.bool === true){
            
            this.counterCorrect++;
            this.currentAmount += array.amount;
            array.bgColor = 'bg-green';
           
         }else{
            array.bgColor = 'bg-red';
            this.counterFalse++;
            setTimeout(()=>{
               this.inGame = false;
            },2000);
            
            this.currentAmount = 0;
         }
      },

      delayNextQuestion:function(array){
         setTimeout(()=>{
         this.nextQuestion();
         
         array.bgColor = '';
      },2000);
   }

},

// mounted(){
//    this.generateRandom()
// }



  
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
       animation: blink 0.3s linear infinite;
   }

   .bg-red{
      background-color: red;
       animation: blink 0.3s linear infinite;
   }

   @keyframes blink{
   0%{opacity: 0.3;}
   50%{opacity: .8;}
   100%{opacity: 1;}
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
      position: relative;
      

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

            .score{
               position: absolute;
               top:80%;
               left: 50%;
               transform: translateX(-50%);
               color: #fff;
            }

            #incorrect-counter{
               position: absolute;
               top: 70%;
               color: #fff;
               left: 50%;
               transform: translateX(-50%);
            }

            #play-again{
               position: absolute;
               background-color: #fff;
               border-radius: 5px;
               padding: 15px;
               color: #000;
               top: 88%;
               left: 50%;
               transform: translateX(-50%);
               cursor: pointer;
            }
      
   }
</style>