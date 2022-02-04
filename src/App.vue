<template>
  <div id="app">
    <header-box @search="searchResults" />
    <main-content
    :moviesCards="moviesResultsList"
    :seriesCards="seriesResultsList"
    :movieSectionTitle="movieSection"
    :tvSEriesSectionTitle="tvSeriesSection"
    />
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
      movieSection: '',
      tvSeriesSection: '',
    };
  },
  mounted() {
    this.generalMovieApiCall('movie', 'popular', 'page', 1)
    this.movieSection = 'I film più popolari su Netflix:'
    this.generalTvApiCall('tv', 'popular', 'page', 1)
    this.tvSeriesSection = 'Le serie Tv più popolari su Netflix:'
  },

  methods: {
    searchResults(keyword){
      this.generalMovieApiCall('search', 'movie', 'query', keyword);
      this.generalTvApiCall('search', 'tv', 'query', keyword);
    },
    
    async generalMovieApiCall(command, type, query, keyword) {
      this.moviesResultsList = await this.callApi(command, type, query, keyword);
    },

    async generalTvApiCall(command, type, query, keyword) {
      this.seriesResultsList = await this.callApi(command, type, query, keyword);
    },

    async callApi(command, type, query, keyword) {

      const results = await axios.get(`https://api.themoviedb.org/3/${command}/${type}?${query}=${keyword}&api_key=${this.api_key}`).then((response) => {
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
