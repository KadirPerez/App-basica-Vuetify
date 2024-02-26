<template>
    <v-data-table :items="datosSimulados"></v-data-table>
</template>

<script>
export default {
  data() {
    return {
      datosSimulados: []
    };
  },
  mounted() {
    this.obtenerDatos();
  },
  methods: {
    async obtenerDatos() {
      try {
        const respuesta = await fetch("https://jsonplaceholder.typicode.com/todos");
        this.datosSimulados = await respuesta.json();
      } catch (error) {
        console.error('Error al obtener los datos:', error);
      }
    }
  }
};
</script>
