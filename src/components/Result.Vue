<template>
  <div>
    <!-- <h1>Masth training. Level {{level + 1}}</h1> -->
    <hr>
    <div class="container-content">
      <span>Success {{count + 1}}</span>
      <span>error {{error + 1}}</span>
      <div class="answer">
        <button class="btn">Repeat</button>
        <button class="btn">Next level</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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

