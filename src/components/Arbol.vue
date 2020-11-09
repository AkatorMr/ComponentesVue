<template>
  <div :class="indice>0?'arbol':''">
    <div>
      <div class="ele"></div>
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
    titulo: String
  },
  data() {
    return {
      re: null,
      fecha: "",
      error: false,
      mostrar: false
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
  margin-top: 8px;
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
  margin-left: 0;
  float: left;
  padding-right: 11px;
}
</style>
