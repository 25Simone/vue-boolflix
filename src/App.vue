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
      // API KEY
      api_key: '0b8af459fa891cf5a8cc79e1ded434fb',
    };
  },
  mounted() {
    // this.generalApiCall(this.moviesResultsList, 'movie/popular', 'page', 1)
  },

  methods: {
    searchResults(keyword){
      this.showMovies(keyword);
      this.showTv(keyword);
    },

    async showMovies(keyword) {
      this.moviesResultsList = await this.callApi('movie', 'query', keyword);
    },

    async showTv(keyword) {
      this.seriesResultsList = await this.callApi('tv', 'query', keyword);
    },

    
    async generalApiCall(list, type, query, keyword) {
      list = await this.callApi(type, query, keyword);
    },

    async callApi(type, query, keyword) {

      const results = await axios.get(`https://api.themoviedb.org/3/search/${type}?${query}=${keyword}&api_key=${this.api_key}`).then((response) => {
        console.log('Api risposta'); // DEBUG
        console.log(response.data.results) // DEBUG
        return response.data.results;
      })
      return results;
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
