<template>
  <div class="wrapper">
    <div class="wrapperBefore"></div>
    <div class="wrapperAfter"></div>

    <div class="mainCard">
      <span class="cardTitle">Country Quiz</span>
      <!-- Stackblitz won't allow non-premium members to upload images to their projects so I used an emoji for the card image -->
      <span class="cardImage">🌍</span>

      <div v-if="!loading" class="questionsWrapper">
  
        <p class="question">
          {{ currentChoices.capital.capital }} is the capital of
          <!-- {{ currentChoices.capital.name }} -->
        </p>

        <p class="answer"><span class="answerCounter">A</span> {{ currentChoices.choiceA.name }}</p>
        <p class="answer">
          <span class="answerCounter">B</span> {{ currentChoices.choiceB.name }}
        </p>
        <p class="answer"><span class="answerCounter">C</span> 
        {{ currentChoices.choiceC.name }}</p>
        <p class="answer"><span class="answerCounter">D</span>
         {{ currentChoices.choiceD.name }}</p>
      </div>
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
      countriesInfo: [],
      error: null,
      loading: false,
      answersCounter: 0,
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
      this.handleCurrentChoices(finalRes);
    },
    handleCurrentChoices(countriesInfo) {
      if (countriesInfo.length) {
        let capital =
          countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];

        let choiceA =
          countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];
        let choiceB =
          countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];
        let choiceC =
          countriesInfo[
            Math.floor(Math.random() * this.countriesInfo.length - 1)
          ];
        let choiceD =
          countriesInfo[
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

let keys = ['choiceA', 'choiceB', 'choiceC', 'choiceD']
        let randomRightAnswer = keys[Math.floor(Math.random() * keys.length - 1)]

       this.currentChoices[randomRightAnswer] = this.currentChoices.capital

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
  font-size: 23px;
}
.answer {
  position: relative;
  width: 100%;
  border: 2px solid navy;
  border-radius: 10px;
  height: 15%;
  display: flex;
  place-items: center;
  color: #724dd5;
}
.question {
  color: navy;
  font-size: 17px;
  font-weight: bolder;
  position: relative;
  width: 100%;
  text-align: left;
  height: 5%;
}
.questionsWrapper {
  top: 9vh;
  margin: auto;
  position: relative;
  width: 85%;
  height: 75%;
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
