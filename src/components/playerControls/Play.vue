<template>
  <button
    @click="changeSongState(true)"
    v-if="!isSongPlaying"
    class="play"
  ></button>
  <button
    @click="changeSongState(false)"
    v-if="isSongPlaying"
    class="pause"
  ></button>
</template>

<script>
export default {
  name: "Play",
  props: ['isSongPlaying'],
  methods: {
    changeSongState(songState) {
      console.log(this.isSongPlaying, "BBB");
      this.$emit("song-state", songState);
    },
  },
};
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
  background-image: url("../../assets/images/controls/icons8-play-96.png");
}
.pause {
  background-image: url("../../assets/images/controls/icons8-pause-96.png");
}
</style>