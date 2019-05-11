<template>
  <div>
    <div class="container-content">
      <h2>Are you ready?</h2>
      <button class="btn btn-starter" @click="$emit('visibleQuestion')">start</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['progres'],
  data() {
    return {};
  },
  methods: {}
};
</script>
<style scoped>
.container-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h2 {
  margin-bottom: 20px;
}
</style>


