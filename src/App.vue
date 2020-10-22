<template>
  <div id="app">
    <NavigationBar class="nb_class" />
    <BarraBusqueda @input="handleSearch" class="app_busqueda" />
    <UsuarioCuenta class="app_usuario" />
    <MusicaDetalle
      class="musica_detalle"
      v-if="currentPodcastAlbun"
      :name="currentPodcastAlbunTracks[0].artist.name"
      :album="currentPodcastAlbunTracks[0].title"
      :url="currentPodcastAlbunTracks[0].preview"
      :image="currentPodcastAlbun.cover_medium"
    />
    <p class="resultados">Resultados</p>

    <div class="mu_podcasts">
      <MuPodcats
        class="mu_podcast"
        v-for="(albun, index) in albunes"
        :key="`albun_${index}`"
        :image="albun.cover_medium"
        :name="albun.title"
        :album="albun.artist.name"
        @click="handleClickPodcast(albun)"
      />
    </div>

    <div v-if="currentPodcastAlbun" class="app-player">
      <FuPlayer
        :name="currentPodcastAlbunTracks[0].artist.name"
        :album="currentPodcastAlbunTracks[0].title"
        :url="currentPodcastAlbunTracks[0].preview"
        :image="currentPodcastAlbun.cover_medium"
      />
    </div>
  </div>
</template>

<script>
import NavigationBar from "./components/NavigationBar";
import FuPlayer from "./components/FuPlayer";
import MusicaDetalle from "./components/MusicaDetalle";
import BarraBusqueda from "./components/BarraBusqueda";
import MuPodcats from "./components/MuPodcats";
import UsuarioCuenta from "./components/UsuarioCuenta";

export default {
  name: "App",
  components: {
    NavigationBar,
    FuPlayer,
    MusicaDetalle,
    BarraBusqueda,
    MuPodcats,
    UsuarioCuenta,
  },
  data() {
    return {
      albunes: [],
      debounce: null,
      currentPodcastAlbun: null, //obtener el albun actual
      currentPodcastAlbunTracks: null, //obtener el track del albun actual
    };
  },

  computed: {
    //obtenerFirstAudioAlbun
    getFIrstClip() {
      return this.currentPodcastAlbun;
    },
  },

  methods: {
    //metodo para traer los tracklist del album seleccionado
    async handleClickPodcast(albun) {
      const { id } = albun;
      const audio_albun = await this.getAudioAlbum(id);
      // Info de album seleccionado
      this.currentPodcastAlbun = albun;
      // Tracks del album seleccionado
      this.currentPodcastAlbunTracks = audio_albun;
    },
    //Metodo para Buscar Albunes
    handleSearch(query) {
      clearTimeout(this.debounce);
      this.debounce = setTimeout(() => {
        fetch(
          "https://cors-anywhere.herokuapp.com/https://api.deezer.com/search/album?q=" +
            query
        )
          .then((response) => response.json())
          .then((data) => {
            this.albunes = data.data;
          });
      }, 500);
    },
    //metodo para obtener el audio del album
    getAudioAlbum(id) {
      return fetch(
        `https://cors-anywhere.herokuapp.com/https://api.deezer.com/album/${id}/tracks`
      )
        .then((response) => response.json())
        .then((data) => data.data);
    },
  },
};
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}
.app-player {
  position: fixed;
  bottom: 0;
  width: 100%;
}
.musica_detalle {
  margin-top: 106px;
  position: absolute;
}
.app_busqueda {
  position: absolute;
  margin-left: 325px;
  margin-right: 406px;
}

.resultados {
  color: #E86060;
  position: absolute;
  width: 118px;
  height: 28px;
  margin-left: 370px;
  margin-top: 396px;
  font-family: Quicksand;
  font-style: normal;
  font-weight: bold;
  font-size: 22px;
  line-height: 27px;
}
.mu_podcasts {
  display: flex;
  flex-wrap: wrap;
  justify-content: start;
  position: absolute;
  margin-top: 444px;
  margin-bottom: 483px;
  margin-left: 370px;
  height: 55vh;
}

.nb_class {
  position: absolute;
}
</style>
