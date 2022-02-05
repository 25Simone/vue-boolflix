<template>
  <main>
    <!-- MOVIES -->
    <div id="movies" class="container-fluid">
      <h1 class="section-title">{{ movieSectionTitle }}</h1>
      <!-- CARDS -->
      <div id="movies-row" class="row">
        <card-box
          v-for="(card, i) in moviesCards"
          :key="i"
          :card="card"
          :name="card.title"
          :originalName="card.original_title"
        />
      </div>
    </div>
    <button @click="moviesGoNext('movies-row')">next</button>
    <button @click="moviesGoPrev('movies-row')">prev</button>

    <!-- TV SERIES -->
    <div id="tv-series" class="container-fluid">
      <h1 class="section-title">{{ tvSEriesSectionTitle }}</h1>
      <!-- CARDS -->
      <div id="tv-series-row" class="row">
        <card-box
          v-for="(card, i) in seriesCards"
          :key="i"
          :card="card"
          :name="card.name"
          :originalName="card.original_name"
        />
      </div>
    </div>
    <button @click="seriesGoNext('tv-series-row')">next</button>
    <button @click="seriesGoPrev('tv-series-row')">prev</button>

  </main>
</template>

<script>
import CardBox from "./CardBox.vue";
export default {
  components: {
    CardBox,
  },
  props: {
    moviesCards: Array,
    seriesCards: Array,
    movieSectionTitle: String,
    tvSEriesSectionTitle: String,
  },
  data() {
    return {
      moviesScrollPosition: 0,
      seriesScrollPosition: 0,
    };
  },
  methods: {
      // NEXT AND PREV BUTTONS FUNCTIONS
    moviesGoNext(rowId) {
      const scrollContainer = document.getElementById(rowId);
      this.moviesScrollPosition++;
      scrollContainer.scrollLeft = window.innerWidth * this.moviesScrollPosition;
    },
    moviesGoPrev(rowId) {
      const scrollContainer = document.getElementById(rowId);
      this.moviesScrollPosition--;
      scrollContainer.scrollLeft = window.innerWidth * this.moviesScrollPosition;
    },

    seriesGoNext(rowId) {
      const scrollContainer = document.getElementById(rowId);
      this.seriesScrollPosition++;
      scrollContainer.scrollLeft = window.innerWidth * this.seriesScrollPosition;
    },
    seriesGoPrev(rowId) {
      const scrollContainer = document.getElementById(rowId);
      this.seriesScrollPosition--;
      scrollContainer.scrollLeft = window.innerWidth * this.seriesScrollPosition;
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  padding-top: 100px;
}
.container-fluid {
  margin: 70px 0;
  .row {
    flex-wrap: nowrap;
    overflow-x: hidden;
    scroll-behavior: smooth;
  }
}
</style>
