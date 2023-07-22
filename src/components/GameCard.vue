<template>
  <div class="wrapper">
  <div class='wrapperBefore'></div>
  <div class='wrapperAfter'></div>
aaaaaaaaaaaaa
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
.wrapper{
  background-color:#3e1d98;
  width:100%;
  height:100vh;
  position:relative;
}
.wrapperBefore{
  width:90vh;
  height:90vh;
  background-color: #724dd5;
  position:absolute;
  top:-20vh;
  right:-50vh;
  transform:rotate(40deg);
  border-radius:25px
}

.wrapperAfter{
  width:90vh;
  height:90vh;
  background-color: #724dd5;
  position:absolute;
  bottom:-40vh;
  left:-30vh;
  transform:rotate(40deg);
  border-radius:25px;
}
</style>
