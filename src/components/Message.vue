<template>
  <div>
    <h1>Message</h1>
    <hr>
    <ProgresBar :progres="progres"></ProgresBar>
    <div class="container-content">
      <span>{{text}}</span>
      <span>{{type}}</span>
      <div class="answer">
        <button class="btn" @click="$emit('nextQuest')">Continue</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  
  props: ["type", "text"],
  data() {
    return {};
  }
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
  justify-content: center;
  align-items: center;
}
</style>

