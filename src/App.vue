<template>
  <div class="container">
    <starting v-if="visible === 'Starting'" v-on:visibleQuestion="visible = 'Question'"></starting>
    <question v-else-if="visible === 'Question'"></question>
    <Result v-else-if="visible === 'Result'"></Result>
    <wright-answer v-else-if="visible === 'WrightAnswer'"></wright-answer>
    <!-- <-wright-answer></-wright-answer> -->
    <!-- <-Result></-Result> -->
    <ProgresBar></ProgresBar>
  </div>
</template>

<script>
import Starting from "./components/Starting.vue";
import Question from "./components/Question.vue";
import Result from "./components/Result.vue";
import WrightAnswer from "./components/WrightAnswer.vue";
import ProgresBar from "./components/ProgresBar.vue";


export default {
  data() {
    return {
      visible: "Starting"
    };
  },
  components: {
    Starting,
    Question,
    Result,
    WrightAnswer,
    ProgresBar
  }
};
</script>


<style>
.container {
  max-width: 650px;
  margin: 0 auto;
  text-align: center;
}
.container-content {
  background-color: #f5f5f5;
  padding: 25px 0;
}
.btn {
  background-color: #00a214;
  border: none;
  padding: 8px 25px;
  border-radius: 5px;
  outline: none;
  cursor: pointer;
  color: #ffffff;
}
</style>
