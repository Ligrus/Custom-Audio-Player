<template>
  <div class="cover second-song"><div class="center"></div></div>
</template>

<script>

export default {
  name: 'Cover'
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
.first-song {
  background-image: url("../../assets/images/hey.jpg");
}
.second-song {
  background-image: url("../../assets/images/summer.jpg");
}
.third-song {
  background-image: url("../../assets/images/ukulele.jpg");
}
</style>