<template>
  <div id="app">
    <header-box
    @search="searchResults"
    :genres="genresList"
    @filterGenres="filterByGenres"
    />
    <trailer-box v-if="movieTrailer" />
    <main-content
    :moviesCards="filteredMoviesResultsList"
    :seriesCards="filteredSeriesResultsList"
    :movieSectionTitle="movieSectionTitle"
    :tvSEriesSectionTitle="tvSeriesSectionTitle"
    />
  </div>
</template>

<script>
import axios from "axios";
import HeaderBox from "./components/HeaderBox.vue";
import MainContent from "./components/MainContent.vue";
import TrailerBox from "./components/TrailerBox.vue";

export default {
  name: "App",
  components: {
    HeaderBox,
    MainContent,
    TrailerBox,
  },
  data() {
    return {
      // SEARCH RESULTS LIST
      movieSectionTitle: '',
      moviesResultsList: [],
      filteredMoviesResultsList: [],
      tvSeriesSectionTitle: '',
      seriesResultsList: [],
      filteredSeriesResultsList: [],
      // API KEY
      api_key: '0b8af459fa891cf5a8cc79e1ded434fb',
      movieTrailer: true,
      // GENRES LIST
      genresList: [],
    };
  },
  mounted() {
    // HOME PAGE WITH POPULAR MOVIES AND TV SERIES
      this.generalMovieApiCall('movie', 'popular', 'page', 1);
      this.movieSectionTitle = 'I film più popolari su Netflix:';
      this.generalTvApiCall('tv', 'popular', 'page', 1);
      this.tvSeriesSectionTitle = 'Le serie Tv più popolari su Netflix:';
      // GENRES LIST
      this.genresApiCall();
  },

  methods: {
    // FUNCTION TO SHOW THE SEARCH'S RESULTS
    searchResults(keyword){
      if(keyword != '') {
        this.generalMovieApiCall('search', 'movie', 'query', keyword);
        this.movieSectionTitle = 'Film in base alla tua ricerca:';
        this.generalTvApiCall('search', 'tv', 'query', keyword);
        this.tvSeriesSectionTitle = 'Serie tv in base alla tua ricerca:';
        this.movieTrailer = false;
      } else {
        this.generalMovieApiCall('movie', 'popular', 'page', 1);
        this.movieSectionTitle = 'I film più popolari su Netflix:';
        this.generalTvApiCall('tv', 'popular', 'page', 1);
        this.tvSeriesSectionTitle = 'Le serie Tv più popolari su Netflix:';
        this.movieTrailer = true;
      }
    },

    // GENRES API CALL
    async genresApiCall() {
      await axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=${this.api_key}&language=en-US`).then((response) => {
        this.genresList = response.data.genres;
      })
    },
    // MOVIES API CALL
    async generalMovieApiCall(command, type, query, keyword) {
      this.moviesResultsList = await this.callApi(command, type, query, keyword);
      this.filteredMoviesResultsList = await this.callApi(command, type, query, keyword);
    },
    // TV SERIES API CALL
    async generalTvApiCall(command, type, query, keyword) {
      this.seriesResultsList = await this.callApi(command, type, query, keyword);
      this.filteredSeriesResultsList = await this.callApi(command, type, query, keyword);
    },

    async callApi(command, type, query, keyword) {

      const results = await axios.get(`https://api.themoviedb.org/3/${command}/${type}?${query}=${keyword}&api_key=${this.api_key}`).then((response) => {
        return response.data.results;
      })
      return results;
    },

    // FUNCTION TO FILTER THE RESULTS BY GENRES
    filterByGenres(keyword){
      this.filteredMoviesResultsList = this.moviesResultsList.filter((element) => {
        return element.genre_ids.includes(keyword) || keyword === 'all';
      });
      this.filteredSeriesResultsList = this.seriesResultsList.filter((element) => {
        return element.genre_ids.includes(keyword) || keyword === 'all';
      });
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
