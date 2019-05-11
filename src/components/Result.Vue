<template>
  <div>
    <div class="container-content">
      <span>Success {{status.success}}</span>
      <span>error {{status.error}}</span>
      <div class="answer">
        <button class="btn" @click="$emit('repeatLevel')">Repeat</button>
        <button class="btn" @click="$emit('nextLevel')">Next level</button>
        <button class="btn">Stats</button>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["status"],

  data() {
    return {
      count: 0,
      error: 0
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

