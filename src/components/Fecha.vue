<template>
  <div class="">
    <input :class="'fecha '+(error?'conerror':'')" @focus="OnFocus" @keypress="key_press" @keydown="key_down" v-model="fecha" @blur="CompletarFecha" />
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
      error:false
    };
  },
  methods: {
    LanzarFechaCompleta:function(){
      console.log("Fecha completa");
    },
    LanzarError:function(){
      console.log("Error en la escritura de la fecha");
    },
    OnFocus:function(){
      this.error = false;
    },
    CompletarFecha:function (){
      //this.fecha+="66";
      let base = this.fecha;
      let cu_fe = this.fecha.split("/");
      let current_date = new Date();
      let dia = "";
      let mes = "000"+(current_date.getMonth()+1)+"";
      let anio = "0000"+current_date.getFullYear();
      mes = ""+mes.substr(mes.length-2).toString();
      
      anio = ""+anio.substr(anio.length-4).toString();
      
      switch(cu_fe.length){
        case 1:
          //Sin barras
          if(cu_fe.length==1 && cu_fe !="0"){
            this.fecha="0"+this.fecha;
            this.fecha+="/"+mes;
            this.fecha+="/"+anio;
          }
          break;
          case 2:
            //Tiene 1 barra osea dia y mes
            dia ="00"+ cu_fe[0];
            this.fecha = dia.substring(dia.length-2)+"/";
            mes = "00" + cu_fe[1];
            this.fecha += mes.substring(mes.length-2)+"/";
            this.fecha+=anio;
            break;
          case 3:
            //Tiene las 2 barras, es decir todos los datos
            dia ="00"+ cu_fe[0];
            
            this.fecha = dia.substring(dia.length-2)+"/";
            if(this.fecha=="00/") {
              this.error = true;
              this.LanzarError();
            }
            mes = "00" + cu_fe[1];
            mes=mes.substring(mes.length-2);
            if(mes=="00") {
              this.error = true;
              this.LanzarError();
            }
            this.fecha += mes + "/";
            anio = "0000" + cu_fe[2];
            let a_num =cu_fe[2].substring(-1)*1;
            if( a_num<99){
              if(a_num<50){
                  anio="0000"+(a_num*1+2000);
              }else{
                anio="0000"+(a_num*1+1900);
              }
            }
            anio = anio.substring(anio.length-4);
            
            if(anio=="0000" && cu_fe[2]!="00") {
              this.error = true;
              this.LanzarError();
            }
            this.fecha += ""+anio;
            break;
      }

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
.fecha.conerror{
  background: rgb(255, 133, 133);
  color:rgb(168, 0, 0);
  border-color: red;
  
}

</style>
