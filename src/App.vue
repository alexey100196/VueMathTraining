<template>
  <div class="container">
    <starting v-if="visible === 'Starting'" v-on:visibleQuestion="visible = 'Question'"></starting>
    <question v-else-if="visible === 'Question'"
      v-on:success="successQuest"
      v-on:error="errorQuest"
    ></question>
    <Result v-else-if="visible === 'Result'"></Result>
    <wright-answer v-else-if="visible === 'WrightAnswer'"></wright-answer>
    <message v-else-if="visible === 'Message'"
     :type="message.type" 
     :text="message.text"
     v-on:nextQuest="visible = 'Question'"
     ></message>
    <!-- <-wright-answer></-wright-answer> -->
    <!-- <-Result></-Result> -->
    <!-- <ProgresBar></ProgresBar> -->
  </div>
</template>

<script>
import Starting from "./components/Starting.vue";
import Question from "./components/Question.vue";
import Result from "./components/Result.vue";
import WrightAnswer from "./components/WrightAnswer.vue";
import Message from "./components/Message.vue";
import ProgresBar from "./components/ProgresBar.vue";

export default {
  data() {
    return {
      visible: "Starting",
      message: {
        type: "",
        text: ""
      }
    };
  },
  methods: {
    successQuest() {
      this.visible = "Message";
      this.message.text = "Good";
      this.message.type = "success-bg";
    },
    errorQuest() {
      this.visible = "Message";
      this.message.text = "Not Good";
      this.message.type = "error-bg";
    }
  },
  components: {
    Starting,
    Question,
    Result,
    WrightAnswer,
    Message,
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

.success-bg {
  background-color: #00a214;
}
.error-bg {
  background-color: #cc3c3c;
}
</style>
