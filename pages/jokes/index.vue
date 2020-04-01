<template>
  <div>
    <Search v-on:search-text="searchText" />
    <div class="box">
      <article class="media">
        <div class="media-content">
          <Joke
            class="content"
            v-for="joke in jokes"
            :key="joke.id"
            :id="joke.id"
            :joke="joke.joke"
          />
        </div>
      </article>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Joke from "@/components/Joke";
import Search from "@/components/Search";

export default {
  components: {
    Joke,
    Search
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
      console.log(res.data);
      this.jokes = res.data.results;
    } catch (error) {
      console.log(error);
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
        console.log(res.data);
        this.jokes = res.data.results;
      } catch (error) {
        console.log(error);
      }
    }
  },
  head() {
    return {
      title: "Jokes",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "best place for corny dad jokes"
        }
      ]
    };
  }
};
</script>

<style></style>
