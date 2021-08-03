<template>
  <CalculatorWrapper />
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CalculatorWrapper from './components/CalculatorWrapper.vue'

export default {
  name: 'App',
  components: {
    CalculatorWrapper,
    // HelloWorld
  }
}
</script>

<style>
body {
  margin: 0px;
  box-sizing: border-box;
}
*, *::after, *::before {
  box-sizing: border-box;
}
#app {
  font-family: Roboto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #a6bcd3;
  background-color: #000e1d;
  width: 100vw;
  max-width:100%;
  height:100vh;
  max-height:100%;
  margin: 0px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
