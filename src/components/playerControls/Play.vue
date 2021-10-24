<template>
  <button class="play"></button>
  <button class="pause"></button>
</template>

<script>

export default {
  name: 'Play',
}
</script>

<style scoped>
button {
  background-position: center;
  background-size: 75px;
  background-repeat: no-repeat;
  background-color: transparent;
  border: none;
  width: 30%;
  height: 96px;
}
.play {
  background-image: url('../../assets/images/controls/icons8-play-96.png');
}
.pause {
  background-image: url('../../assets/images/controls/icons8-pause-96.png');
}
</style>