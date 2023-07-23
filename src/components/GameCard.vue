<template>
  <div class="wrapper">
  <div class='wrapperBefore'></div>
  <div class='wrapperAfter'></div>



  <div class='mainCard'>
  <span class='cardTitle'>Country Quiz</span>
  <!-- Stackblitz won't allow non-premium members to upload images to their projects so I used an emoji for the card image -->
  <span class='cardImage'>🌍</span>


  <div class='questionsWrapper'>
  <p class='question'> WORK IN PROGRESS is the capital of</p>
  <p  class='answer'> <span class='answerCounter'>A</span>aaaaaaaaa</p>
   <p class='answer'><span class='answerCounter'>B</spanbbbbbbbbbbbbbbb</p> 
   <p class='answer'><span class='answerCounter'>C</spanccc</p>
    <p class='answer'><span class='answerCounter'>D</spandddddddddd</p>
  </div>

  </div>

    <p class='explanation'>Challenge created by Pascu Ioana with Vue and Stackblitz for <a href='https://devchallenges.io/challenges/Bu3G2irnaXmfwQ8sZkw8'>DevChallenges -> Front End Developer Path</a></p>
  </div>
</template>

<script>
export default {
  name: 'GameCard',
  props: {
    // msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
  padding:0px;
  margin:0px;
}
.answer:hover{
  cursor:pointer;
  color:white;
  background:orange;
  border:2px solid orange;

}
.answer:hover > *{
  color:white;
}
.answerCounter{
  color:#724dd5;
  font-weight:bolder;
  padding:0px 3vh;
  font-size:23px;
}
.answer{
  position:relative;
  width:100%;
  border:2px solid navy;
  border-radius:10px;
  height:15%;
  display:flex;
  place-items:center;

}
.question{
  color:navy;
  font-size:17px;
  font-weight:bolder;
  position:relative;
  width:100%;
  text-align:left;
  height:5%;
  
}
.questionsWrapper{
  top:9vh;
  margin:auto;
  position:relative;
  width:85%;
  height:75%;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  align-items:center;
}
.cardImage{
  font-size:18vh;
  position:absolute;
  right:-2vh;
  top:-16vh;
}
.cardTitle{
  text-transform:uppercase;
  font-weight:bolder;
  color:white;
  font-size:25px;
  position:absolute;
 top:-7vh;
}
.mainCard{
  background-color:white;
  width:65vh;
  height: 75vh;
  z-index:6;
  position: relative;
  top:14vh;
  margin:auto;
  border-radius:20px;
}
.wrapper{
  background-color:#3e1d98;
  width:100%;
  height:100vh;
  position:relative;
  overflow:hidden;

}
.wrapperBefore{
  width:90vh;
  height:90vh;
  background-color: #724dd5;
  position:absolute;
  top:-20vh;
  right:-50vh;
  transform:rotate(40deg);
  border-radius:25px;
}

.wrapperAfter{
  width:90vh;
  height:90vh;
  background-color: #724dd5;
  position:absolute;
  right:60vh;
  margin-top:40vh;
  transform:rotate(40deg);
  border-radius:25px;
}
.explanation{
  font-size:12px;
  z-index:5;
  color:white;
  opacity:0.8;
  padding: 4vh 0vh;
  position:absolute;
  bottom:0px;
  text-align:center;
  width:100%;
}
a, a:active, a:hover, a:visited{
  color: white;
}
</style>
