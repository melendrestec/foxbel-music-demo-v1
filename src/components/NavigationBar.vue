<template>
  <div class="navigationBar">
    <img
      class="navigation_bar_logo"
      src="../assets/foxbel.png"
      alt="Foxbel-music Logo"
    />
    <div class="texto-container">
      <div class="navigation_bar_texto">
        <p class="navigation_bar_lib">Mi librería</p>
        <p class="navigation_bar_recents">Recientes</p>
        <p>Artistas</p>
        <p>Albunes</p>
        <p>Estaciones</p>
      </div>
      <div class="navigation_bar_texto_2">
        <p class="navigation_bar_lib">Play List</p>
        <p>Metal</p>
        <p>Para bailar</p>
        <p>Rock 90s</p>
        <p>Baladas</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "navigationBar",
};
</script>


<style scoped>
.navigationBar {
  width: 330px;
  height: 1087px;
  background: #662323;
  display: flex;
  justify-content: center;
  position: absolute;
}
.texto-container {
  font-size: 16px;
  line-height: 20px;
}

.navigation_bar_logo {
  width: 250px;
  height: 59px;
  margin-left: 40px;
  margin-right: 40px;
  margin-top: 50px;
}
.navigation_bar_texto {
  position: absolute;
  width: 75px;
  height: 20px;
  left: 40px;
  top: 171px;
  font-family: Quicksand;
  font-style: normal;
  font-size: 16px;
  line-height: 20px;
  color: #FFFFFF;
}
.navigation_bar_texto_2 {
  position: absolute;
  width: 77px;
  height: 28px;
  left: 40px;
  top: 420px;
  font-family: Quicksand;
  font-size: 16px;
  line-height: 20px;
  color: #FFFFFF;
}

.navigation_bar_lib {
  width: 111px;
  height: 28px;
  left: 40px;
  top: 139px;
  color: #FFFFFF;
  font-family: Quicksand;
  font-style: normal;
  font-weight: bold;
  font-size: 22px;
  line-height: 27px;
}
.navigation_bar_recents {
  color: #E86060;
}
</style>