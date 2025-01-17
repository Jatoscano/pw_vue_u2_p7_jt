<template>
  <img
    :src="imagen"
    alt="Imagen no vista"
  />

  <div class="seccion-pregunta">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
    <p>Recuedra de cuando finalice la pregunta da un "?"</p>

    <h1>{{ pregunta }}</h1>
    <h2>{{ respuesta }}</h2>
  </div> 
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
img {
  max-height: 100%;
  height: 100vh;
  max-width: 100%;
  width: 100vw;
  position: fixed;
  top: 0px;
  left: 0px;
}

.seccion-pregunta {
  position: relative;
}

h1, h2, p {
  color: white;
}

p{
  font-size: 30px;
}

input {
  margin-top: 35%;
  width: 260px;
  padding: 15px 30px;
  border: none;
  border-radius: 7px;
  font-size: 18px;
}
</style>