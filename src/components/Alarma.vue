<template>
  <div
    :class="'col Alarma '+(armada?'Alarma-Armada':'') +(blink&&armada?' Alarma-Blink':'') "
  >{{nombre}}</div>
</template>
<script lang="ts">
export default {
  name: "Alarma",
  props: {
    nombre: String,
    armada: Boolean,
    blink: Boolean
  },
  methods: {}
};
</script>
<style scoped>
.Alarma {
  width: 150px;
  height: 150px;
  background-color: grey;
  flex: auto;
  float: right;
}
.Alarma.Alarma-Armada {
  background-color: rgb(252, 116, 116);
}
.Alarma.Alarma-Armada.Alarma-Blink {
  background-color: red;
}
</style>