<template>
  <div class="container">
    <div></div>
    <div class="progress-container">
      <h4></h4>
      <div class="progress">
        <div class="progress-amount"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProgressBar',
  props: {
    next: {type: Boolean, default: false}
  }
}
</script>

<style scoped>
.container {
  position: absolute;
  width: 80%;
  height: 45px;
  background-color: bisque;
  border-radius: 12px;
}
</style>