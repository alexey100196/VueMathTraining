<template>
  <div>
    <div class="tracks_list">
      <div class="track func_progress" data-final="70">
        <div class="progress_bar">
          <i v-bind:style="{'width': progresBar + '%' }"></i>
        </div>
        <span>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["progresBar"],
  data() {
    return {};
  }
};
</script>
<style scoped>
.tracks_list {
  margin-bottom: 10px;
}
.progress_bar,
i {
  background: #e3e3e3;
  height: 14px;
  position: relative;
  border-radius: 10px;
  margin-bottom: 10px;
  transition: .3s;
}
i {
  display: flex;
  background-color: #add136;
  position: absolute;
  width: 10px;
}
</style>


