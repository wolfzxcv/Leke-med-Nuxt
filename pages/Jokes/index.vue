<template>
  <div>
    <SearchJokes v-on:search-text="searchText" />
    <Joke v-for="x in jokes" :key="x.id" :id="x.id" :joke="x.joke" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke";
import SearchJokes from "../../components/SearchJokes";

export default {
  components: {
    Joke,
    SearchJokes
  },
  data() {
    return {
      jokes: []
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);

      this.jokes = res.data.results;
      console.log("api request when mount", this.jokes);
    } catch (err) {
      console.log(err);
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };
      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        );

        this.jokes = res.data.results;
        console.log("api request when mount", this.jokes);
      } catch (err) {
        console.log(err);
      }
    }
  },
  head() {
    return {
      title: "Dad Jokes",
      meta: [
        {
          hid: "description",
          name: "name here of jokes page",
          content: "Best place for corny dad jokes"
        }
      ]
    };
  }
};
</script>

<style>
</style>
