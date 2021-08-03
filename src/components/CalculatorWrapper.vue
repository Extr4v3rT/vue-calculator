<template>
  <div class="wrapper">
      <TopBar />
      <ResultDisplay :result="result" :math="math" />
      <ButtonSection :result="result" :math="math" @resultClear="resultClear" @mathCalc="mathCalc" @result="resultFunc" />
  </div>
</template>

<script>
import TopBar from './TopBar.vue'
import ResultDisplay from './ResultDisplay.vue'
import ButtonSection from './ButtonsSection.vue'
import { evaluate } from 'mathjs';

// import { evaluate } from 'mathjs'

export default {
  name: "CalculatorWrapper",
  components: {
      TopBar,
      ResultDisplay,
      ButtonSection,
  },
  data: function() {
    return {
      result: 0,
      math: 0,
    }
  },
  methods: {
    resultClear() {
      this.result = 0;
      this.math = 0;
    },
    mathCalc(numbers) {
      this.math = numbers;
    },
    resultFunc(e) {
      if(e.type == "divideZero") {
        this.math = e.text;
      } else {
        this.result = evaluate(e);
        this.math = this.result;
      }
    }
  }
};
</script>

<style scoped>
.wrapper {
  width: 350px;
  height: 550px;
  background-color: #0b1e31;
  border-radius: 20px;
  border: 2px solid rgb(11, 184, 144);
  box-shadow: 0px 0px 42px 8px rgba(18, 227, 179, .5);
  overflow: hidden;
}

@media screen and (max-width: 400px) {
  .wrapper {
    width: 100vw;
    height: 100vh;
  }
}
</style>