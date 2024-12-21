<template>
  <img
    :src="imagen"
    alt="Imagen no vista"
  />
  <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
  <p>Recuedra de cuando finalice la pregunta da un "?"</p>

  <h1>{{ pregunta }}</h1>
  <h2>{{ respuesta }}</h2>
</template>

<script>
export default {
  data() {
    return {
      pregunta: "Hola Mundo",
      respuesta: null,
      imagen: "https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif"
    };
  },

  watch: {
    pregunta(newValue, oldValue) {
      console.log(newValue, oldValue);
      if (newValue.includes("?")) {
        console.log("Es una pregunta");
        //Programar la llamada a la API
        //Para obtener la respuesta y la imagen
        console.log("Aqui llamo al API");
        this.llamaApi();
      }
    },
  },

  methods: {
    async llamaApi() {
      console.log("Aqui llamo al API");
      const data = await fetch("https://yesno.wtf/api").then((response) =>response.json());

      this.respuesta = data.answer;
        this.imagen = data.image;
      console.log(data);
    },

    async fachada(){
        await this.llamaApi();
    }
  },
};
</script>

<style>
</style>