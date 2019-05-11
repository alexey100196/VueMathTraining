<template>
  <div>
    <div class="container-content">
      <span>{{x}} + {{y}} = ?</span>
      <div class="answer">
        <button
          class="btn"
          v-for="(item, i) in numbers"
          :key="i"
          @click="clickAnswer(item)"
        >{{item}}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      x: this.randomNumber(),
      y: this.randomNumber(),
      // progres: 30
    };
  },
  methods: {
    randomNumber(min, max) {
      return Math.floor(Math.random() * (10 - 1 + 1)) + 1;
    },
    clickAnswer(num) {
      if (num === this.x + this.y) {
        this.$emit("success");
      } else {
        this.$emit("error");
      }
    },
  },
  computed: {
    numbers() {
      let rightAnswer = this.x + this.y;
      let result = [rightAnswer];

      while (result.length < 2) {
        let rand = this.randomNumber();

        if (result.indexOf(rand) === -1) {
          result.push(rand);
        }
      }

      return result.sort((a, b) => Math.random() - 0.5);
    }
  },
};
</script>
<style scoped>
span {
  display: block;
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 50px;
}
.answer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 50%;
  margin: 0 auto;
}
</style>

