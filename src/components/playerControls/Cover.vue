<template>
  <div  class="cover" :style="{background: `url:(${songCover})`}"><div class="center"></div></div>
</template>

<script>

export default {
  name: 'Cover',
  props: ['songCover'],
  watch: {
    songCover(value) {
      console.log(value, 'COVER')
    }
  }
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
}

</style>