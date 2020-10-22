<template>
  <div class="fu-player">
    <img :src="image" :alt="name" class="fu-player_image" />
    <div class="fu-player_details">
      <p class="fu-player_name">{{ name }}</p>
      <p class="fu-player_album">{{ album }}</p>
    </div>

    <div class="fu-player_play" v-on:click="handlePodcast">
      <div class="fu-Izquierda">
        <i class="fas fa-angle-double-left"></i>
      </div>
      <i v-show="isPaused" class="fas fa-play"></i>
      <i v-show="!isPaused" class="fas fa-pause"></i>
      <div class="fu-Derecha">
        <i class="fas fa-angle-double-right"></i>
      </div>
    </div>
    <div class="fu-player_volumen">
      <input
        class="fu-player_volumenRange"
        type="range"
        min="0"
        max="100"
        v-model="volume"
        v-on:input="setVolume"
      />
      <div v-on:click="toggleVolume" class="fu-player_volumenIcon">
        <i v-show="volume > 0" class="fas fa-volume-up"></i>
        <i v-show="volume == 0" class="fas fa-volume-mute"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FuPlayer",

  props: {
    name: {
      type: String,
      required: true,
    },
    album: {
      type: String,
      required: true,
    },
    url: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
  },

  data() {
    return {
      audio: new Audio(this.url),
      isPaused: true,
      volume: 50,
    };
  },
  watch: {
    url: function (newVal, oldVal) {
      if (newVal !== oldVal) {
        this.audio.src = this.url;
        if (!this.isPaused) {
          this.audio.play();
        }
      }
    },
  },
  methods: {
    handlePodcast() {
      if (this.audio.paused) {
        this.audio.play();
        this.isPaused = false;
      } else {
        this.audio.pause();
        this.isPaused = true;
      }
    },
    setVolume() {
      console.log(this.volume);
      this.audio.volume = this.volume / 100;
    },
    toggleVolume() {
      if (this.audio.muted) {
        this.volume = 100;
        this.audio.muted = false;
      } else {
        this.volume = 0;
        this.audio.muted = true;
      }
      this.setVolume();
    },
  },
};
</script>

<style scoped>
.fu-player {
  display: grid;
  grid-template-columns: 100px repeat(3, 1fr);
  background: #EB5757;
  width: 100%;
  height: 100px;
}
.fu-player_image {
  width: 100px;
  height: 100px;
  object-fit: cover;
  vertical-align: top;
}
.fu-player_details {
  margin-left: 20px;
  color: #fff;
  align-self: center;
}
.fu-player_name {
  margin-left: 20px;
  font-weight: bold;
  font-size: 14px;
  color: #fff;
}
.fu-player_album {
  font-weight: 500;
  font-family: Quicksand;
  font-size: 12px;
  margin-left: 20px;
  color: #fff;
}
.fu-player_play {
  align-self: center;
  justify-self: center;
  color: #fff;
  font-size: 20px;
  background: #FF7676;
  height: 60px;
  width: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  cursor: pointer;
}
.fu-Derecha {
  position: absolute;
  width: 20.4px;
  height: 20.4px;
  left: 725.2px;
  top: 39.2px;
}

.fu-Izquierda {
  position: absolute;
  width: 20.4px;
  height: 20.4px;
  margin-left: -60px;
  margin-right: 48.8px;
  top: 39.2px;
}
.fu-player_volumen {
  display: flex;
  align-items: center;
  margin-right: 32px;
  justify-self: end;
}

.fu-player_volumenIcon {
  color: #fff;
  font-size: 20px;
  margin-left: 40px;
}

.fu-player_volumenRange {
  color: #FFFFFF;
  appearance: none;
  outline: none;
  border-radius: 8px;
  height: 6px;
  cursor: pointer;
}
</style>