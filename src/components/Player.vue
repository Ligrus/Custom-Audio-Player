<template>
  <audio @timeupdate="updateSongTime" ref="audio"></audio>
  <div class="player-container">
    <progress-bar :playedTime="songElapsedTime" @song-position-update="updateSongPosition"></progress-bar>
    <div class="player">
      <div class="player__cover">
        <cover :songCover="activePlayingSong.img"></cover>
      </div>
      <div class="player__controls">
        <next-song @change-song="playPreviousSong" ></next-song>
        <play @song-state="playSong" :is-song-playing="isSongPlaying"></play>
        <next-song @change-song="playNextSong" next></next-song>
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
          src: "music/hey.mp3",
        },
        {
          img: "../assets/images/summer.jpg",
          name: "summer",
          src: "music/summer.mp3",
        },
        {
          img: "../assets/images/ukulele.jpg",
          name: "ukulele",
          src: "music/ukulele.mp3",
        },
      ],
      activeSong: 0,
      songElapsedTime: 0,
      isSongPlaying: false
    };
  },
  methods: {
    playSong(songState) {
      this.isSongPlaying = songState
      if (this.isSongPlaying) {
        this.$refs.audio.play();
        return
      }
      this.$refs.audio.pause();
    },
    playPreviousSong() {
      if(this.activeSong === 0) {
        return
      }
      this.activeSong = this.activeSong - 1
      this.isSongPlaying = true
      this.initAudio()
      this.$refs.audio.play();
    },
    playNextSong() {
      if(this.activeSong === this.songs.length - 1) {
        return
      }
      this.activeSong = this.activeSong + 1
      this.isSongPlaying = true
      this.initAudio()
      console.log(this.activePlayingSong, 'hhh', this.activeSong)
      this.$refs.audio.play();
    },
    updateSongTime(e) {
      this.songElapsedTime = (e.target.currentTime / e.target.duration) * 100
    },
    updateSongPosition(updatedPosition) {
      const audioPlayer = this.$refs.audio;
      audioPlayer.currentTime = audioPlayer.duration * updatedPosition
    },
    initAudio() {
      const audioPlayer = this.$refs.audio;
      console.log(audioPlayer, 'FFF')
      audioPlayer.src = this.activePlayingSong.src;
      audioPlayer.type = 'audio/mp3'
    },
  },
  computed: {
    activePlayingSong: function () {
      return this.songs[this.activeSong];
    },
  },
   watch: {
    songElapsedTime(value) {
      if (value === 100) {
        this.isSongPlaying = false
        this.songElapsedTime = 0
      }
    }
  },
  mounted() {
    this.initAudio()
    // I'm text inside the component.
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
