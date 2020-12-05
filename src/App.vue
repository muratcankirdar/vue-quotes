<script>
import QuoteContainer from './components/QuoteContainer.vue';

export default {
  name: 'App',

  components: {
    QuoteContainer,
  },

  data: () => ({
    //
  }),
};
</script>

<template>
  <v-app>
    <v-app-bar
      color="#fef0e5"
      app
    >
      <span>Random Quote App</span>

      <v-spacer></v-spacer>

      <a href="https://type.fit/api/quotes" target="_blank" class="text-decoration-none">API</a>
    </v-app-bar>

    <v-main>
      <QuoteContainer/>
    </v-main>
  </v-app>
</template>
