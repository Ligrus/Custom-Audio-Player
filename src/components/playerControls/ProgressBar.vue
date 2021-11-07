<template>
  <div class="container">
    <div class="space-block"></div>
    <div class="progress-container">
      <h4>hello</h4>
      <div @click="changeSongTime($event)" class="progress-bar">
        <div class="progress-bar-indicator" :style="{width: `${playedTime}%`}"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProgressBar',
  props: {
    playedTime: {type: Number, default: 0}
  },
  methods: {
    changeSongTime(e) {
      const progressBarCoords = e.target.getBoundingClientRect()
      const widthClickPosition = (e.x - progressBarCoords.left) / progressBarCoords.width
      this.$emit("song-position-update", widthClickPosition);
    }
  }
}
</script>

<style scoped>
 
h4 {
  margin: 0;
}
.container {
  position: absolute;
  display: flex;
  align-items: center;
  width: 27%;
  height: 55px;
  background-color: bisque;
  border-radius: 12px 12px 0 0;
  top: -60%;
  left: 50%;
  transform: translateX(-50%);
}

.space-block {
  width: 40%
}

.progress-container {
  width: 60%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  height: 100%
}

.progress-bar {
  height: 4px;
  background-color: gray;
  border-radius: 5px;
  margin-top: 10px;
  cursor: pointer;
  width: 95%;
}

.progress-bar-indicator {
  height: 100%;
  width: 100%;
  background-color: red;
  border-radius: 5px
}

</style>