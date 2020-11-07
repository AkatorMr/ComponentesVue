<template>
  <div class="arbol">
    <div>{{titulo}}</div>
    <slot class="desplegable">No Disponible!</slot>
  </div>
</template>

<script>

export default {
  name: "Arbol",
  components:{
    
  },
  props:{
    indice:Number,
    titulo:String
  },
  data() {
    return {
      re: null,
      fecha: "",
      error:false
      
    };
  },
  methods: {
    Indice:function(){
      return this.indice+1;
    },
    
  },
  mounted() {
    console.log("Mounted");
    this.re = new RegExp("[0-9/]");
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.arbol{
  margin-left:45px;
}
.arbol .desplegable{
  margin-left:15px;
}
</style>
