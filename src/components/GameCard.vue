<template>
  <div class="wrapper">
  <div class='wrapperBefore'></div>
  <div class='wrapperAfter'></div>

  <div class='mainCard'>
  <span class='cardTitle'>Country Quiz</span>
  <span class='cardImage'>🌍</span>
  ssss
  </div>

    <p>Challenge created by Pascu Ioana with Vue and Stackblitz for <a href='https://devchallenges.io/challenges/Bu3G2irnaXmfwQ8sZkw8'>DevChallenges -> Front End Developer Path</a></p>
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
.cardImage{
  font-size:20vh;
  position:absolute;
  right:-2vh;
  top:-15vh;
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
  width:60vh;
  height: 65vh;
  z-index:6;
  position: relative;
  top:15vh;
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
p{
  z-index:5;
  color:white;
  opacity:0.8;
  padding: 10vh 10vh;
  position:absolute;
  bottom:0px;
  text-align:center;
}
a, a:active, a:hover, a:visited{
  color: white;
}
</style>
