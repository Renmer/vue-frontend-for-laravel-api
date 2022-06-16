<template>
  <v-app>
    
    <v-app-bar app color="#BA0000" dark>
      Vue + Vuetify
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>

  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
