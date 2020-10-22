<template>
  <div id="app">
    <div class="fu-player">
      <img v-bind:src="image" :alt="name" class="fu-player_image" />
      <div class="fu-player_details">
        <p class="fu-player_name">{{ name }}</p>
        <p class="fu-player_album">{{ album }}</p>
        <div class="play_detalle">
          <i class="fas fa-play"></i>
        </div>
        <div class="clases_buton">
          <input type="button" value="Reproducir" class="button_reproducir" />
          <input type="button" value="Seguir" class="button_seguir" />
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "MusicaDetalle",

  props: {
    image: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    album: {
      type: String,
      required: true,
    },
  },
};
</script>


<style scoped>
.play_detalle {
  width: 63px;
  height: 72px;
  margin-left: 0px;
  top: 89px;
}
.detalle_musica {
  background: #EB5757;
  margin-left: 370px;
  margin-right: 40px;
  margin-top: 90px;
  width: 890px;
  height: 250px;
  position: absolute;
  opacity: 50%;
}
.fu-player {
  display: grid;
  grid-template-columns: 100px repeat(2, 1fr);
  background: #EB5757;
  width: 890px;
  height: 250px;
  margin-left: 370px;
  margin-right: 40px;
  margin-top: 106px;
}

.fu-player_image {
  width: 250px;
  height: 250px;
  object-fit: cover;
  vertical-align: top;
}

.fu-player_details {
  margin-left: 20px;
  color: #fff;
  align-self: flex-start;
}
.fu-player_name {
  margin-left: 200px;
  margin-top: 40px;
  font-weight: bold;
  font-size: 14px;
  color: #fff;
  text-align: left;
}

.fu-player_album {
  font-weight: 500;
  font-family: Quicksand;
  font-size: 12px;
  margin-left: 60px;
  color: #fff;
}
.button_reproducir {
  background: #E86060;
  border-radius: 100px;
  margin-top: 100px;
  width: 117px;
  height: 31px;
  font-family: Quicksand;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 17px;
  color: #FFFFFF;
}

.button_seguir {
  margin-left: 20px;
  margin-top: 100px;
  background: #E86060;
  border: 1px solid #EB5757;
  box-sizing: border-box;
  border-radius: 100px;
  width: 117px;
  height: 31px;
  font-family: Quicksand;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 17px;
  color: #FFFFFF;
}

.clases_buton {
  margin-top:-65px;
  display: flex;
  flex-wrap: wrap;
  margin-left: 121px;
  align-items: center;
  text-align: center;
}
</style>