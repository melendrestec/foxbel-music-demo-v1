<template>
  <div class="buscador_cabecera">
    <input
      type="text"
      :value="value"
      @input="$emit('input', $event.target.value)"
      class="buscador"
      placeholder="Buscar Musica"
    />
    <div class="buscador_icono">
      <i class="fas fa-search"></i>
    </div>
  </div>
</template>


<script>
export default {
  name: "BarraBusqueda",
  props: ["value"],
};
</script>

<style scoped>
.buscador {
  position: absolute;
  background: #FFFFFF;
  border: 1px solid #828282;
  box-sizing: border-box;
  border-radius: 100px;
  width: 524px;
  height: 36px;
  margin-top: 30px;
  margin-left: 40px;
  margin-right: 406px;
  padding-left: 20px;
}
.buscador_icono {
  position: absolute;
  color: #BDBDBD;
  margin-left: 530px;
  margin-right: 70px;
  margin-top: 39px;
  font-style: normal;
  font-weight: 900;
  font-size: 18px;
  line-height: 21px;
  cursor: pointer;
}
</style>>

