<!-- A base de HTML -->
<template>
  <h2>{{ this.titulo }}</h2>
  <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputed }}</p>
  <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputed }}</p>
  <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputed }}</p>
  <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputed }}</p>
  <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputed }}</p>
    <div>
        <button v-on:click="incrementar()">+1</button>
        <button v-on:click="decrementar()">-1</button>
    </div>
</template>

<!-- A base de JavaScript -->
<script>
export default {
  data() {
    return {
      numero: 10,
      titulo: "Contador",
    };
  },

  methods: {
    calcularCuadrado() {
        console.log("Método calcularCuadrado");
      return this.numero * this.numero;
    },
    incrementar() {
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },

  computed:{
    calcularCuadradoComputed(){
        console.log("Método calcularCuadradoComputed");
        return this.numero * this.numero;
    }
  }
};
</script>

<!-- A base de CSS -->
<style>
h2 {
  box-shadow: #64B687 5px 5px 5px;
  color: blue;
}
p {
  color: red;
}
div {
  margin-top: 20px;
}
button {
    background-color: #64B687;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    margin: 0px 5px;
    padding: 5px 10px;   
}

button:hover {
    background-color: #5AA67B;
}
</style>