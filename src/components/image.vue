<template>
  <div class="container">
    <div>
      <v-card class="mx-auto" max-width="300">
        <v-img
          class="align-end text-white"
          height="450"
          width="300"
          :src="imageUrl"
          cover
        >
        </v-img>

        <v-card-subtitle class="pt-3">
          Chuck Norris Joke
        </v-card-subtitle>

        <v-card-text class="chiste-text">
          {{ chiste }}
        </v-card-text>
      </v-card>
    </div>

    <div>
      <v-btn @click="refrescarTodo">Refrescar Imagen y Chiste</v-btn>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageUrl: '',
      chiste: ''
    };
  },
  methods: {
    async refreshImage() {
      const response = await fetch('https://picsum.photos/200/300');
      this.imageUrl = response.url;
    },
    async obtenerChiste() {
      const respuesta = await fetch('https://api.chucknorris.io/jokes/random');
      const datos = await respuesta.json();
      this.chiste = datos.value;
    },
    async refrescarTodo() {
      await this.refreshImage(); // Refrescar la imagen
      await this.obtenerChiste(); // Obtener un nuevo chiste
    }
  },
  mounted() { 
    this.refrescarTodo();
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column; 
  justify-content: center;
  align-items: center;
  height: 100vh; 
}
.container > div {
  margin-bottom: 10px; 
}

.chiste-text {
  max-height: 100px; /* Limita la altura máxima del texto del chiste */
  overflow-y: auto; /* Agrega una barra de desplazamiento vertical si el texto del chiste es más largo */
}
</style>
