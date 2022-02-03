<template>
  <div id="app">
    <header-box @search="searchResults" />
    <main-content :moviesCards="moviesResultsList" :seriesCards="seriesResultsList" />
  </div>
</template>

<script>
import axios from "axios";
import HeaderBox from "./components/HeaderBox.vue";
import MainContent from "./components/MainContent.vue";

export default {
  name: "App",
  components: {
    HeaderBox,
    MainContent,
  },
  data() {
    return {
      // SEARCH RESULTS LIST
      moviesResultsList: [],
      seriesResultsList: [],
    };
  },
  methods: {
    searchResults(keyword) {
        axios
        .get(
          `https://api.themoviedb.org/3/search/movie?query=${keyword}&api_key=0b8af459fa891cf5a8cc79e1ded434fb`
        )
        .then((response) => {
          console.log(response.data.results); // DEBUG
          this.moviesResultsList = response.data.results;
        });

        axios
        .get(
          `https://api.themoviedb.org/3/search/tv?query=${keyword}&api_key=0b8af459fa891cf5a8cc79e1ded434fb`
        )
        .then((response) => {
          console.log(response.data.results); // DEBUG
          this.seriesResultsList = response.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
