<template>
  <div :class="(indice>0?'arbol':'') + ' ' +(conborde?'conborde':'')">
    <div>
      <div :class="'ele'+' '+(conborde?'conborde':'')"></div>
      <span class="btn btn-sm btn-outline-primary" v-on:click="mostrar^=true;">{{titulo}}</span>
    </div>
    <div class="desplegable" v-if="mostrar">
      <slot>No Disponible!</slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "Arbol",
  components: {},
  props: {
    indice: Number,
    titulo: String,
    conborde: Boolean
  },
  data() {
    return {
      re: null,
      fecha: "",
      error: false,
      mostrar: true
    };
  },
  methods: {
    Indice: function() {
      return this.indice + 1;
    }
  },
  mounted() {
    console.log("Mounted");
    this.re = new RegExp("[0-9/]");
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.arbol {
  /*margin-left: 30px;*/
  /*padding-top: 8px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 1px;*/
}
.desplegable .arbol.conborde:first-child {
  padding-top: 8px;
  border-left-color: black;

  border-left-style: dashed;
  border-left-width: 1px;
}
div.arbol.conborde + div.arbol.conborde {
  padding-top: 8px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 1px;
}
div.arbol.conborde ~ div:not(.arbol.conborde) {
  padding-top: 8px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 0px;
  background-color: blue;
}

div.desplegable > div.arbol.conborde:last-of-type {
  background-color: red;
}
.desplegable {
  padding-left: 30px;
}

.arbol .ele {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #2c3e50;
  width: 0;
  height: 7px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 1px;
  border-bottom: 1px dashed black;
  content: "";
  margin-bottom: 0;
  margin-left: -0;
  float: left;
  padding-right: 11px;
}
.ele2 {
  float: left;
}
.ele2::before {
  content: "";
  width: 0px;
  height: 0px;

  border-right: 50px solid transparent;
  border-top: 50px solid transparent;
  border-left: 1px dashed darkblue;
  border-bottom: 1px dashed darkblue;
  float: left;
}
</style>
