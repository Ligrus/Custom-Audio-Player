<template>
  <audio ref="audio"></audio>
  <div class="player-container">
    <progress-bar></progress-bar>
    <div class="player">
      <div class="player__cover">
        <cover :songCover="activePlayingSong.img"></cover>
      </div>
      <div class="player__controls">
        <next-song></next-song>
        <play @song-state="playSong" :is-song-playing="isSongPlaying"></play>
        <next-song next></next-song>
      </div>
    </div>
  </div>
</template>

<script>
import NextSong from "@/components/playerControls/NextSong.vue";
import Play from "@/components/playerControls/Play";
import Cover from "@/components/playerControls/Cover";
import ProgressBar from "@/components/playerControls/ProgressBar";

export default {
  name: "Player",
  data: function () {
    return {
      songs: [
        {
          img: "../assets/images/hey.jpg",
          name: "hey",
          src: "assets/music/hey.mp3",
        },
        {
          img: "../assets/images/summer.jpg",
          name: "summer",
          src: "assets/music/summer.mp3",
        },
        {
          img: "../assets/images/ukulele.jpg",
          name: "ukulele",
          src: "assets/music/ukulele.mp3",
        },
      ],
      activeSong: 0,
      isSongPlaying: false
    };
  },
  methods: {
    playSong(songState) {
      this.isSongPlaying = songState
      if (this.isSongPlaying) {
        const audioPlayer = this.$refs.audio;
        window.audioPLl = audioPlayer
        audioPlayer.src = this.activePlayingSong.src;
        audioPlayer.type = 'audio/mp3'
        audioPlayer.play();
        return
      }
    },
  },
  computed: {
    activePlayingSong: function () {
      return this.songs[this.activeSong];
    },
  },
  components: { ProgressBar, Cover, NextSong, Play },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.player-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 90%;
}
.player {
  height: 90px;
  background-color: bisque;
  border-radius: 12px;
  width: 30%;
  display: flex;
}
.player__cover {
  position: relative;
  width: 30%;
}
.player__controls {
  display: flex;
  width: 70%;
  align-items: center;
  justify-content: center;
}
</style>
