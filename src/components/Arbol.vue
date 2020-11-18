<template>
  <div :class="(indice>0?'arbol':'') + ' ' +(conborde?'conborde':'')">
    <div>
      <div :class="'hroot'+' '+(conborde?'conborde':'vroot')"></div>
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
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #2c3e50;
}
.desplegable .arbol.conborde:first-child {
  padding-top: 8px;
  border-left-color: black;

  border-left-style: dashed;
  border-left-width: 1px;
}
.conborde {
  padding-top: 8px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 1px;
}

.desplegable {
  padding-left: 30px;
}
.desplegable .arbol.conborde:last-child {
  border-left-width: 0px;
}
.desplegable > div:not(.arbol) {
  position: relative;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 1px;
  padding-left: 5px;
}
.desplegable > div:not(.arbol)::before {
  border-left: 1px dashed black;
  position: absolute;
  border-bottom: 1px dashed black;
  bottom: 0px;
  left: 0px;
  width: 17px;
  height: 0px;

  contain: content;
  content: "";
}

.arbol .hroot {
  width: 0;
  border-bottom: 1px dashed black;
  content: "";
  margin-bottom: 0;
  margin-left: -0;
  float: left;
  padding-right: 11px;
}

.arbol .vroot {
  width: 0;
  height: 12px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 1px;

  content: "";
  margin-bottom: 0;
  margin-left: -0;
  float: left;
  padding-right: 11px;
}

.arbol .ele {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #2c3e50;
  width: 0;
  height: 8px;
  border-left-color: black;
  border-left-style: dashed;
  border-left-width: 0px;
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
