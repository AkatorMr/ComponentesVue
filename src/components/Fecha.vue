<template>
  <div class>
    <input @keypress="key_press" @keydown="key_down" v-model="fecha" @blur="CompletarFecha" />
  </div>
</template>

<script>


export default {
  name: "Fecha",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      re: null,
      fecha: "",
    };
  },
  methods: {
    CompletarFecha:function (){
      this.fecha+="66";
    },
    VerificarGrupoCompleto: function(next){
      let p = this.fecha.split("/");
      console.log(p);
      switch(p.length){
        case 1:
          //sin barras
          //console.log(p[0]>3);
        return p[0]>3 || (p[0]==3 && next != 1);
        case 2:
          //Con 1 barra
          return p[1]>1 || (p[1]==1 && next >2);
        case 3:

          return false;
      }
      return false;
    },
    key_press: function (e) {
      //console.log(e);
      if (e.stopPropagation && !this.re.test(e.key)) {
        e.stopPropagation();
        e.preventDefault();
      } else {
        console.log(this.fecha);

        if (e.key == "/") {
          if (this.fecha.length == 0) {
            //si no hay nada escrito salir
            e.stopPropagation();
            e.preventDefault();
            return;
          } else if (this.fecha.charAt(this.fecha.length - 1) == "/") {
            //Si el ultimo caracter es una barra salir
            e.stopPropagation();
            e.preventDefault();
            return;
          }
          if (this.fecha.split("/").length >= 3) {
            //Si ya están las dos primeras barras terminar
            e.stopPropagation();
            e.preventDefault();
            return;
          }
        }


        if (this.fecha.length == 0) {
          // no tiene nada
          if (e.key == "/") {
            e.stopPropagation();
            e.preventDefault();
          }
        } else {
          // if (this.fecha.length ==2) {
          //   if (e.key != "/") {
          //     if (this.fecha.charAt(this.fecha.length - 1) != "/")
          //       this.fecha += "/";
          //   }
          // }else if (this.fecha.length ==5) {
          //   if (e.key != "/") {
          //     if (this.fecha.charAt(this.fecha.length - 1) != "/")
          //       this.fecha += "/";
          //   }
          // }
          if (e.key != "/") {
            //Entra un nuevo numero
            if(this.VerificarGrupoCompleto(e.key)){
              
              this.fecha+="/";
            }
          }
        }
      }
    },
    key_down: function (e) {
      //console.log(this.re.test(e.key));
      //return true;
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
h1,
h2 {
  font-weight: normal;
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
</style>
