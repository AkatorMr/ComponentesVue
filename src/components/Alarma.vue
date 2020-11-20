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

  padding: 0.75rem 0.75rem;
  margin: 0.5rem;
  border: 1px solid transparent;
  border-radius: 0.25rem;

  color: #0c5460;
  background-color: #d1ecf1;
  border-color: #bee5eb;
}
.Alarma.Alarma-Armada {
  background-color: #f8d7da;
  border-color: #f5c6cb;
  color: #721c24;
}
.Alarma.Alarma-Armada.Alarma-Blink {
  background-color: #d84150;
}
</style>