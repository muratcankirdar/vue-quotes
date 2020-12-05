<script>
import axios from 'axios';

export default {
  name: 'Quote',
  data() {
    return {
      isInitialized: false,
      quotes: [],
      quote: '',
      error: '',
    };
  },
  computed: {
    message() {
      let message = '';

      if (this.error !== '') {
        message = this.error;
      } else if (this.quote.author) {
        message = `${this.quote.author} - ${this.quote.text}`;
      } else {
        message = `Anonymous - ${this.quote.text}`;
      }

      return message;
    },
  },
  mounted() {
    this.getQuotes();
  },
  methods: {
    getQuotes() {
      this.isInitialized = false;
      axios.get('https://type.fit/api/quotes')
        .then((response) => {
          this.quotes = response.data;
          this.selectQuote();
        })
        .catch(() => {
          this.error = 'An error occurred.';
        })
        .finally(() => {
          this.isInitialized = true;
        });
    },
    selectQuote() {
      const randomIndex = this.getRandomInt(this.quotes.length);
      this.quote = this.quotes[randomIndex];
    },
    getRandomInt(max) {
      return Math.floor(Math.random() * Math.floor(max));
    },
    copyQuote() {
      navigator.clipboard.writeText(this.quote.text);
    },
  },
};
</script>

<template>
  <v-row justify="center" class="pa-2">
    <v-col class="text-center">
      <v-row justify="center" align="center">
        <span v-if="isInitialized" class="subtitle-1">
          {{ message }}
        </span>
      </v-row>

      <v-row justify="center" align="center" class="mt-4">
        <v-btn color="primary" outlined @click="selectQuote" class="mx-2">New Quote</v-btn>
        <v-btn color="success" outlined @click="copyQuote" class="mx-2 hidden-sm-and-down">
          Copy
        </v-btn>
      </v-row>
    </v-col>
  </v-row>
</template>

<style>

</style>
