<template>
  <div class="wrapper">
    <div class="wrapperBefore"></div>
    <div class="wrapperAfter"></div>

    <div class="mainCard" v-if='roundsCounter < 5'>
      <span class="cardTitle">Country Quiz</span>
      <!-- Stackblitz won't allow non-premium members to upload images to their projects so I used an emoji for the card image -->
      <span v-if='!isFlagQuestion' class="cardImage">🌍</span>
      <span v-else class="cardImage flagImage">{{currentChoices.capital.flag}}</span>

      <div v-if="!loading" class="questionsWrapper">
        <p v-if='isFlagQuestion' class="question">
       Which country does this flag belong to?
          {{ currentChoices.capital.name }}
      
        </p>
        <p v-else class="question">
          {{ currentChoices.capital.capital }} is the capital of
          {{ currentChoices.capital.name }}
        </p>

        <p
          :class="{
            'answer': true,
            'answerRight': isRightAnswerA,
            'answerWrong': isWrongAnswerA,
            'disabledHover': disabledHoverA,
          }"
          @click="pickAnswer(currentChoices.choiceA, 'A')"
        >
          <span class="answerCounter">A</span> {{ currentChoices.choiceA.name }}
            <p :class="{'choiceDot': visibleChoiceDotA}">{{choiceIconA}}</p>
        </p>

        <p
          :class="{
            'answer': true,
            'answerRight': isRightAnswerB,
            'answerWrong': isWrongAnswerB,
            'disabledHover': disabledHoverB,
          }"
          @click="pickAnswer(currentChoices.choiceB, 'B')"
        >
          <span class="answerCounter">B</span> {{ currentChoices.choiceB.name }}
            <p :class="{'choiceDot': visibleChoiceDotB}">{{choiceIconB}}</p>
        </p>

        <p
          :class="{
            'answer': true,
            'answerRight': isRightAnswerC,
            'answerWrong': isWrongAnswerC,
            'disabledHover': disabledHoverC,
          }"
          @click="pickAnswer(currentChoices.choiceC, 'C')"
        >
          <span class="answerCounter">C</span> {{ currentChoices.choiceC.name }}
            <p :class="{'choiceDot': visibleChoiceDotC}">{{choiceIconC}}</p>
        </p>

        <p
          :class="{
            'answer': true,
            'answerRight': isRightAnswerD,
            'answerWrong': isWrongAnswerD,
            'disabledHover': disabledHoverD,
          }"
          @click="pickAnswer(currentChoices.choiceD, 'D')"
        >
          <span class="answerCounter">D</span>
           {{ currentChoices.choiceD.name }}
          <p :class="{'choiceDot': visibleChoiceDotD}">{{choiceIconD}}</p>
        </p>
      </div>
      <button v-if='visibleNextButton' :class="{'nextButton':visibleNextButton}" @click='goToNext()'>Next</button>
    </div>

      <div class="mainCard" v-else>
      <span class="cardTitle">Country Quiz</span>
      <p class='endImage'> 🌍</p>
      <h1 class='endResults'>Results</h1>
      <p class='endResultsNumber'>You're got <span class='endResultsSpan'> {{answersCounter}}</span> correct answers</p>
      <button class='tryAgain' @click='tryAgain()'>Try again</button>
      </div>



    <p class="explanation">
      Challenge created by Pascu Ioana with Vue and Stackblitz for
      <a href="https://devchallenges.io/challenges/Bu3G2irnaXmfwQ8sZkw8"
        >DevChallenges -> Front End Developer Path</a
      >
    </p>
  </div>
</template>

<script>
export default {
  name: 'GameCard',
  props: {
    // msg: String
  },
  data() {
    return {
      isFlagQuestion:true,
      countriesInfo: [],
      error: null,
      loading: false,
      answersCounter: 0,
      roundsCounter:0,
      visibleNextButton:false,
      isRightAnswerA: false,
      isRightAnswerB: false,
      isRightAnswerC: false,
      isRightAnswerD: false,
      isWrongAnswerA: false,
      isWrongAnswerB: false,
      isWrongAnswerC: false,
      isWrongAnswerD: false,
      disabledHoverA: false,
      disabledHoverB: false,
      disabledHoverC: false,
      disabledHoverD: false,
           visibleChoiceDotA:false,     
           visibleChoiceDotB:false,     
           visibleChoiceDotC:false,
      visibleChoiceDotD:false,
      choiceIconA:'',
      choiceIconB:'',
      choiceIconC:'',
      choiceIconD:'',
      currentChoices: {
        capital: {},
        choiceA: {},
        choiceB: {},
        choiceC: {},
        choiceD: {},
      },
    };
  },
  mounted() {
    this.getCountriesInfo();
  },
  methods: {
    async getCountriesInfo() {
      this.loading = true;
      const res = await fetch(
        'https://restcountries.com/v3.1/all?fields=name,flag,capital'
      );
      const finalRes = await res.json();
      this.countriesInfo = await finalRes;
      this.loading = false;
      this.handleCurrentChoices();
    },
  tryAgain(){
    console.log('aaaaa')
    this.goToNext()
    this.answersCounter = 0
    this.roundsCounter = 0
  },
goToNext(){
  // console.log('go to next')
      this.visibleNextButton=false,
      this.isRightAnswerA= false,
      this.isRightAnswerB=false,
      this.isRightAnswerC=false,
      this.isRightAnswerD=false,
      this.isWrongAnswerA=false,
      this.isWrongAnswerB=false,
      this.isWrongAnswerC=false,
      this.isWrongAnswerD= false,
      this.disabledHoverA= false,
      this.disabledHoverB= false,
      this.disabledHoverC= false,
     this.disabledHoverD= false,
           this.visibleChoiceDotA=false,     
           this.visibleChoiceDotB=false,     
           this.visibleChoiceDotC=false,
      this.visibleChoiceDotD=false,
      this.choiceIconA='',
      this.choiceIconB='',
      this.choiceIconC='',
      this.choiceIconD='',
      this.currentChoices= {
        capital: {},
        choiceA: {},
        choiceB: {},
        choiceC: {},
        choiceD: {},
      },
      this.handleCurrentChoices()
},
    pickAnswer(choice, letter) {

      if(this.roundsCounter < 5){

      this.roundsCounter++
        this.disabledHoverA = true,
        this.disabledHoverB = true,
        this.disabledHoverC = true,
        this.disabledHoverD = true,
        this.visibleNextButton = true
         console.log(this.roundsCounter, 'rounds')

      if (this.currentChoices.capital.capital === choice.capital) {
        this.answersCounter++
        console.log(this.answersCounter)
        switch (letter) {
          case 'A':
            this.isRightAnswerA = true;
            this.visibleChoiceDotA = true;
            this.choiceIconA = '✓'
            break;
          case 'B':
            this.isRightAnswerB = true;
            this.visibleChoiceDotB = true;
            this.choiceIconB = '✓'
            break;
          case 'C':
            this.isRightAnswerC = true;
            this.visibleChoiceDotC = true;
            this.choiceIconC = '✓'
            break;
          case 'D':
            this.isRightAnswerD = true;
            this.visibleChoiceDotD = true;
            this.choiceIconD = '✓'
            break;
        }
      }
       else if (this.currentChoices.capital.capital !== choice.capital) {
          let winningKey;
        for (const [key, value] of Object.entries(this.currentChoices)) {
          if (
            value['capital'] === this.currentChoices.capital.capital &&
            key !== 'capital'
          ) {
            winningKey = key.toString().slice(-1);
          }
        }
        switch (winningKey) {
          case 'A':
            this.isRightAnswerA = true;
            this.visibleChoiceDotA = true;
            this.choiceIconA = '✓'
            break;
          case 'B':
            this.isRightAnswerB = true;
            this.visibleChoiceDotB = true;
            this.choiceIconB = '✓'
            break;
          case 'C':
            this.isRightAnswerC = true;
            this.visibleChoiceDotBC = true;
            this.choiceIconC = '✓'
            break;
          case 'D':
            this.isRightAnswerD = true;
           this.visibleChoiceDotD = true;
            this.choiceIconD = '✓'
            break;
        }
        switch (letter) {
          case 'A':
            this.isWrongAnswerA = true;
            this.visibleChoiceDotA = true;
            this.choiceIconA = '✖'
            break;
          case 'B':
            this.isWrongAnswerB = true;
            this.visibleChoiceDotB = true;
            this.choiceIconB = '✖'
            break;
          case 'C':
            this.isWrongAnswerC = true;
            this.visibleChoiceDotC = true;
            this.choiceIconC = '✖'
            break;
          case 'D':
            this.isWrongAnswerD = true;
            this.visibleChoiceDotD = true;
            this.choiceIconD = '✖'
            break;
        }
      }
      }
      else if (this.roundsCounter >= 5){
        console.log('more than 5 rounds')
      }
    },
    handleCurrentChoices() {
      if (this.countriesInfo.length) {
        let capital =
          this.countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];

        let choiceA =
          this.countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];
        let choiceB =
          this.countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];
        let choiceC =
          this.countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];
        let choiceD =
          this.countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];

        this.currentChoices.capital = {
          name: capital.name.common,
          flag: capital.flag,
          capital: capital.capital[0],
        };
        this.currentChoices.choiceA = {
          name: choiceA.name.common,
          flag: choiceA.flag,
          capital: choiceA.capital[0],
        };
        this.currentChoices.choiceB = {
          name: choiceB.name.common,
          flag: choiceB.flag,
          capital: choiceB.capital[0],
        };
        this.currentChoices.choiceC = {
          name: choiceC.name.common,
          flag: choiceC.flag,
          capital: choiceC.capital[0],
        };
        this.currentChoices.choiceD = {
          name: choiceD.name.common,
          flag: choiceD.flag,
          capital: choiceD.capital[0],
        };

        let keys = ['choiceA', 'choiceB', 'choiceC', 'choiceD'];
        let randomRightAnswer = keys[Math.floor(Math.random() * keys.length)];

        this.currentChoices[randomRightAnswer] = this.currentChoices.capital;

      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  padding: 0px;
  margin: 0px;
  letter-spacing: 1px;
  font-family: Verdana;
}
.flagImage{
  font-size:130px !important;
  position:absolute;
  top:-14vh !important;
  right:1vh !important;

}
.tryAgain{
  color:navy;
  border:2px solid navy;
  border-radius:5px;
  padding:15px 25px;
  background:transparent;
  cursor:pointer;
  margin-left:35%;
  position:absolute;
  bottom:7vh;
}
.endResultsSpan{
  color:#31bd54;
  font-size:25px;
  font-weight:bold;
}
.endResultsNumber{
  color:navy;
  text-align:center;
}
.endResults{
  text-align:center;
  padding:15px 0px;
  padding-top:40px;
  color:navy;
}
.endImage{
  font-size:120px;
  text-align:center;
  padding-top:2vh;
}
.nextButton{
  background:orange;
  padding:12px 20px;
  color:white;
  font-weight:bolder;
  font-size:14px;
  border:none;
  border-radius:6px;
  position:absolute;
  bottom:4vh;
  right:5vh;
  cursor:pointer;
}
.choiceDot{
  background:transparent;
  font-size:18px;
  border:2px solid white;
  color:white;
  width:23px;
  height:23px;
  border-radius:50%;
  position:absolute;
  right:20px;
  display:flex;
  justify-content:center;
  align-items:center;
  font-weight:normal;
}
.disabledHover {
  pointer-events: none !important;
}
.answerWrong {
  color: white !important;
  background: #d54d63;
  border: 2px solid #d54d63 !important;
}
.answerWrong > *,
.answerRight > * {
  color: white !important;
}
.answerRight {
  color: white !important;
  background: #63d54d;
  border: 2px solid #63d54d !important;
}
.answerRight:hover {
  color: white !important;
  background: #63d54d;
  border: 2px solid #63d54d !important;
}
.answer:hover {
  cursor: pointer;
  color: white;
  background: orange;
  border: 2px solid orange;
}
.answer:hover > * {
  color: white;
}
.answerCounter {
  color: #724dd5;
  font-weight: bolder;
  padding: 0px 3vh;
  font-size: 20px;
}
.answer {
  position: relative;
  width: 100%;
  border: 2px solid navy;
  border-radius: 10px;
  height: 13%;
  display: flex;
  place-items: center;
  color: #724dd5;
  font-weight: bold;
  font-size: 14px;
}
.question {
  color: navy;
  font-size: 16px;
  font-weight: bolder;
  position: relative;
  width: 100%;
  text-align: left;
  height: 5%;
  margin-bottom:5%;
}
.questionsWrapper {
  top: 9vh;
  margin: auto;
  position: relative;
  width: 85%;
  height: 70%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
.cardImage {
  font-size: 18vh;
  position: absolute;
  right: -2vh;
  top: -16vh;
}
.cardTitle {
  text-transform: uppercase;
  font-weight: bolder;
  color: white;
  font-size: 25px;
  position: absolute;
  top: -7vh;
}
.mainCard {
  background-color: white;
  width: 65vh;
  height: 75vh;
  z-index: 6;
  position: relative;
  top: 14vh;
  margin: auto;
  border-radius: 20px;
}
.wrapper {
  background-color: #3e1d98;
  width: 100%;
  height: 100vh;
  position: relative;
  overflow: hidden;
}
.wrapperBefore {
  width: 90vh;
  height: 90vh;
  background-color: #724dd5;
  position: absolute;
  top: -20vh;
  right: -50vh;
  transform: rotate(40deg);
  border-radius: 25px;
}

.wrapperAfter {
  width: 90vh;
  height: 90vh;
  background-color: #724dd5;
  position: absolute;
  right: 60vh;
  margin-top: 40vh;
  transform: rotate(40deg);
  border-radius: 25px;
}
.explanation {
  font-size: 12px;
  z-index: 5;
  color: white;
  opacity: 0.8;
  padding: 4vh 0vh;
  position: absolute;
  bottom: 0px;
  text-align: center;
  width: 100%;
}
a,
a:active,
a:hover,
a:visited {
  color: white;
}
</style>
