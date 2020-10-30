<template>
  <div class="tabla">
    <input
      v-for="i in range(19)"
      v-bind:key="i"
      @keyup="Organizar"
      @keydown="Entrada($event, i)"
      ref="Celda"
      v-model="valores[i]"
    />
  </div>
</template>

<script>
export default {
  name: "Tabla",
  data() {
    return {
      re: null,
      fecha: "",
      error: false,
      valores: [],
      l_id: -1,
    };
  },
  methods: {
    range: function (n) {
      let ran = [];
      for (let i = 0; i < n; i++) {
        ran.push(i);
      }
      return ran;
    },
    Organizar: function (event) {
      if (this.l_id >= 0) {
        //Aca hay que separar
        //si tiene tab -> solo separar por tab
        // si no tiene tab -> separar primero por grupo de () y luego por espacios
        console.log(this.valores[this.l_id]);
        let texto = this.valores[this.l_id];
        let celda_inicial = this.l_id;

        this.valores[this.l_id] = "";
        //ANTES hay que separarlos por filas y a cada uno por tab o " "
        if (texto.includes("\t")) {
          //Contiene tabs asi que hay que separarlos por eso
          let reg = new RegExp("\t");
          let parts = texto.split(reg);
          console.log(parts);
          for (let part = 0; part < parts.length; part++) {
            this.valores[celda_inicial + part] = parts[part];
            //console.log(this.valores);
            this.$refs["Celda"][part + celda_inicial].value = parts[part];
          }
          console.log(this.valores);
        }

        this.l_id = -1;
        return true;
      }
    },

    Entrada: function (event, id) {
      if (event.ctrlKey && event.key == "v") {
        //Pegados
        this.l_id = id;
        //console.log(this.texto[id]);
      }
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
.tabla {
  display: inline-block;
  width: 438px;
}
.tabla input {
  width: 100px;
}
</style>
