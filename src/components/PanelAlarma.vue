<template>
  <div class="container">
    <div class="row">
      <alarma
        v-for="(item,key) in Alarmas"
        :nombre="item.nombre"
        :armada="item.armada"
        :blink="Blink==1"
        v-bind:key="key"
      ></alarma>
    </div>
  </div>
</template>
<script lang="">
import Alarma from "./Alarma.vue";

export default {
  name: "PanelAlarma",
  components: {
    Alarma
  },
  data() {
    return {
      timer: -1,
      Alarmas: [],
      Blink: false
    };
  },
  methods: {
    TimerCallback: function() {
      this.Blink ^= true;
    }
  },
  mounted() {
    if (this.timer == -1) this.timer = setInterval(this.TimerCallback, 1000);
    else {
      clearInterval(this.timer);
      this.timer = setInterval(this.TimerCallback, 1000);
    }

    this.Alarmas.push({ nombre: "Temperatura", armada: true });
    this.Alarmas.push({ nombre: "Joder", armada: false });
    this.Alarmas.push({ nombre: "Viento", armada: false });
    this.Alarmas.push({ nombre: "Sin Señal", armada: false });
    this.Alarmas.push({ nombre: "Sin Plata", armada: true });
    this.Alarmas.push({ nombre: "Agua", armada: false });
    this.Alarmas.push({ nombre: "Transformador", armada: true });

    this.Alarmas.push({ nombre: "Sin Plata", armada: true });
    this.Alarmas.push({ nombre: "Agua", armada: false });
    this.Alarmas.push({ nombre: "Transformador", armada: true });
    this.Alarmas.push({ nombre: "Temperatura", armada: true });
    this.Alarmas.push({ nombre: "Joder", armada: false });
    this.Alarmas.push({ nombre: "Viento", armada: false });
    this.Alarmas.push({ nombre: "Sin Señal", armada: false });
  }
};
</script>