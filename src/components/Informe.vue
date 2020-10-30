<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Informe',
  props: {
    msg: String,
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}


.resaltar-icono{
  color:#ff8815;
}
.icono-normal{
  color:#d7d7d7;
}
.icono-seleccionado{
  color:#96bad7;
}
.icono-deshabilitado{
  color:#717171;
}

.borde-boton-seleccionado{
  color:#e68a00;
}
.fondo-boton{
  color:#555555;
}
.fondo-programa{
  color:#333333;
}
.borde-separador-fondo{
  color:#333333;
}
.separador{
  border-top-color: #222222;
  border-bottom-color: #828282;
  border-top-width: 1px;
  border-bottom-width: 1px;
  border-style: solid;
  border-left-style:solid;
  border-left-width: 14px;
  border-left-color: transparent;
  border-
}

</style>
