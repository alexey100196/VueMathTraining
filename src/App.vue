<template>
  <div class="container">
    <h1>Math training. Level {{level}}</h1>
    <hr>
    <ProgresBar :progresBar="progresBar"></ProgresBar>
    <transition name="switch" mode="out-in">
      <starting v-if="visible === 'Starting'" v-on:visibleQuestion="visible = 'Question'"></starting>
      <question
        v-else-if="visible === 'Question'"
        v-on:success="successQuest"
        v-on:error="errorQuest"
        :progres="progres"
      ></question>
      <Result
        v-else-if="visible === 'Result'"
        :status="status"
        v-on:nextLevel="nextLevel"
        v-on:repeatLevel="repeatLevel"
      ></Result>
      <wright-answer v-else-if="visible === 'RightAnswer'"></wright-answer>
      <message
        v-else-if="visible === 'Message'"
        :type="message.type"
        :text="message.text"
        :success="status.success"
        :error="status.error"
        v-on:nextQuest="nextQuestion"
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
      level: 1,
      progresBar: 0,
      progres: 0
    };
  },
  computed: {},
  methods: {
    successQuest() {
      this.visible = "Message";
      this.message.text = "Success: " + (this.status.success += 1);
      this.progresBar += 34;
      if (this.progresBar >= 100) {
        this.progresBar = 100;
      }
      this.progres += 1;
    },
    errorQuest() {
      this.visible = "Message";
      this.message.text = "Error: " + (this.status.error += 1);
      this.progresBar -= 20;
      if (this.progresBar <= 0) {
        this.progresBar = 0;
      }
      this.progres += 1;
    },
    nextQuestion() {
      if (this.progresBar == 100) {
        this.progres = 0;
        this.progresBar = 0;
        this.visible = "Result";
      } else {
        this.visible = "Question";
      }
    },
    nextLevel() {
      this.visible = "Question";
      this.level += 1;
    },
    repeatLevel() {
      this.visible = "Question";
      this.level = 1;
      this.status.success = 0;
      this.status.error = 0;
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
  transition: all 0s;
}
.switch-enter,
.switch-leave-to {
  transform: rotateY(-90deg);
}
</style>
