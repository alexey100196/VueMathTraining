<template>
  <div>
    <div class="container-content">
      <button class="btn btn-countine" @click="$emit('visiblAppQuestion')">countine</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style scoped>
.container-content {
  background-color: #f87878;
  padding: 25px 0;
}
</style>

