<template>
  <div class="">
    <input @keypress="key_press" @keydown="key_down" v-model="fecha">
  </div>
</template>

<script>
export default {
  name: 'Fecha',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      re:null,
      fecha:""
    }
  },
  methods: {
    key_press:function(e){
      //console.log(e);
      if (e.stopPropagation && !this.re.test(e.key)) {
        e.stopPropagation();
        e.preventDefault();

      }else{
        console.log(this.fecha.length);
        console.log(this.fecha);
        if(this.fecha.length==0){
          // no tiene nada
          if(e.key=="/"){
            e.stopPropagation();
            e.preventDefault();
          }
        }else{
          if(this.fecha.length==2){
            if(e.key!="/"){
              if(this.fecha.charAt(this.fecha.length-1)!="/")
              this.fecha+="/";
            }
          }
        //es un digito o la barra inversa
        let sp = this.fecha.split("/");
        if(sp.length==0){
          //no tiene /

        }else {
          //Tiene al menos una
        }
        }

      }
     
    },
    key_down:function(e){
      //console.log(this.re.test(e.key));
      //return true;
    }
  },
  mounted(){
    console.log("Mounted");
    this.re = new RegExp("[0-9/]");
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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
