<template>
  <div class="player-container">
    <progress-bar></progress-bar>
    <div class="player">
      <div class="player__cover">
        <cover></cover>
      </div>
      <div class="player__controls">
        <next-song></next-song>
        <play></play>
        <next-song next></next-song>
      </div>
    </div>
  </div>
</template>

<script>
import NextSong from '@/components/playerControls/NextSong.vue'
import Play from "@/components/playerControls/Play";
import Cover from "@/components/playerControls/Cover";
import ProgressBar from "@/components/playerControls/ProgressBar";

export default {
  name: 'Player',
  components: {ProgressBar, Cover, NextSong, Play},
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.player-container  {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 90%
}
.player {
  height: 90px;
  background-color: bisque;
  border-radius: 12px;
  width: 30%;
  display: flex
}
.player__cover {
  position: relative;
  width: 30%
}
.player__controls {
  display: flex;
  width: 70%;
  align-items: center;
  justify-content: center;
}
</style>
