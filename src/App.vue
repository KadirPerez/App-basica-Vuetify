<template>
  <v-card>
    <v-layout>
      <v-navigation-drawer
        expand-on-hover
        rail
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://comunicacioninstitucional.uabc.mx/sites/default/files/inline-images/escudo-actualizado-2022.png"
            title="Super tarea"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" router>
          <v-list-item prepend-icon="mdi-home" to="/" title="Home"></v-list-item>
          <v-list-item prepend-icon="mdi-image" to="/image" title="Imagen"></v-list-item>
          <v-list-item prepend-icon="mdi-table" to="/table" title="Tabla"></v-list-item>
        </v-list>
        
      </v-navigation-drawer>

      <v-main>
        <router-view />
      </v-main>

    </v-layout>
  </v-card>
</template>

<script setup>
  //
</script>