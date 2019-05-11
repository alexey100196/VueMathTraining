<template>
  <div>
    <!-- <h1>Masth training. Level {{level + 1}}</h1> -->
    <h1>Message</h1>
    <hr>
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
  props: ['type', 'text'],
  data() {
    return {
   
    };
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
  justify-content: space-between;
  align-items: center;
  width: 50%;
  margin: 0 auto;
}
</style>

