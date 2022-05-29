<template>
  <v-app>
    <v-app-bar
      app
      flat
      dark
    >
      <v-app-bar-title>
        My Note
      </v-app-bar-title>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
