<template>
  <div class="container">
    <h1>Math training. Level</h1>
    <hr>
    <ProgresBar :progres="progres"></ProgresBar>
    <transition name="switch" mode="out-in">
      <starting v-if="visible === 'Starting'" v-on:visibleQuestion="visible = 'Question'"></starting>
      <question
        v-else-if="visible === 'Question'"
        v-on:success="successQuest"
        v-on:error="errorQuest"
        :progres="progres"
      ></question>
      <Result v-else-if="visible === 'Result'"></Result>
      <wright-answer v-else-if="visible === 'RightAnswer'"></wright-answer>
      <message
        v-else-if="visible === 'Message'"
        :type="message.type"
        :text="message.text"
        :success="status.success"
        :error="status.error"
        v-on:nextQuest="visible = 'Question'"
      ></message>
    </transition>
  </div>
</template>

<script>
import Starting from "./components/Starting.vue";
import Question from "./components/Question.vue";
import Result from "./components/Result.vue";
import RightAnswer from "./components/RightAnswer.vue";
import Message from "./components/Message.vue";
import ProgresBar from "./components/ProgresBar.vue";

export default {
  data() {
    return {
      visible: "Starting",
      message: {
        type: "",
        text: ""
      },
      status: {
        success: 0,
        error: 0
      },
      progres: 0
    };
  },
  methods: {
    successQuest() {
      this.visible = "Message";
      this.message.text = "Success: " + (this.status.success += 1);
      this.progres += 33.333;
    },
    errorQuest() {
      this.visible = "Message";
      this.message.text = "Error: " + (this.status.error += 1);
      this.progres += 33.333;
    }
  },
  components: {
    Starting,
    Question,
    Result,
    RightAnswer,
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



/* Animation */
.switch-enter-active,
.switch-leave-active {
  transition: all 0.3s;
}
.switch-enter,
.switch-leave-to {
  opacity: 0;
}
</style>
