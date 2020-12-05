<script>
import Quote from './Quote.vue';

export default {
  name: 'QuoteContainer',

  components: {
    Quote,
  },
  data() {
    return {
      //
    };
  },
};
</script>

<template>
  <v-container fill-height fluid>
    <Quote />
  </v-container>
</template>

<style scoped lang="scss">
</style>
