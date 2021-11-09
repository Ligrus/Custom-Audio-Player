<template>
  <button @click="changesong" :class="{'next-song': next, 'previous-song': !next}"></button>
</template>

<script>

export default {
  name: 'NextSong',
  props: {
    next: {type: Boolean, default: false}
  },
  methods: {
    changesong() {
      this.$emit("change-song");
    }
  }
}
</script>

<style scoped>
button {
  background-position: center;
  background-size: 45px;
  background-repeat: no-repeat;
  background-color: transparent;
  border: none;
  width: 30%;
  height: 96px;
}
.next-song {
  background-image: url("../../assets/images/controls/icons8-fast-forward-96.png");
}
.previous-song {
  background-image: url("../../assets/images/controls/icons8-rewind-96.png");
}
</style>