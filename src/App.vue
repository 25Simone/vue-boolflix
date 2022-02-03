<template>
  <div id="app">
    <header-box @search="searchResults" />
    <main-content :cards="resultsList" />
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
      resultsList: [],
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
          this.resultsList = response.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
