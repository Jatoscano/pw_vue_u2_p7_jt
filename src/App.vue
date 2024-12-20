<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!--HelloWorld msg="Welcome Juan Toscano"/-->
  <Contador encabezado="Contador Primero" v-bind:valor=calcular(1,3) :esVerdad="muestra1"></Contador>
  <Contador encabezado="Contador Segundo" :valor="5+1" :esVerdad="muestra2" :valor2="78"/>
  <Contador encabezado="Contador Tercero" :valor="6+1" :esVerdad="true"/>

  <button @:click="cambiar(1)">Cambiar Primero</button>
  <button @:click="cambiar(2)">Cambiar Segundo</button>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Contador from "./components/Contador.vue"

export default {
  name: "App",
  components: {
    //HelloWorld
    Contador,
  },
  methods: {
    calcular(a,b){
      return a+b;
    },
    cambiar(valor){
      if(valor == 1){
        this.muestra1 = !this.muestra1;
      }else{
        this.muestra2 = !this.muestra2;
      }

    }

  },
  data() {
    return {
      muestra1: true,
      muestra2: true,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
