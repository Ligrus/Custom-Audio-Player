<template>
  <div  class="cover" :style="{backgroundImage: `url(${songCover})`, animationPlayState: isSongPlaying ? 'running' : 'paused'}"></div>
</template>

<script>

export default {
  name: 'Cover',
  props: ['songCover', 'isSongPlaying']
}
</script>

<style scoped>
.cover {
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  border-radius: 50%;
  border: none;
  height: 96px;
  width: 96px;
  position: absolute;
  border: 3px solid #cdc1c1;
  top: -35%;
  left: 25%;
  animation: rotate 3s linear infinite;
}
@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(359deg);
  }
}
</style>