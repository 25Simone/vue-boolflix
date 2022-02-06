<template>
  <main>
    <!-- MOVIES -->
    <div id="movies" class="container-fluid">
      <h1 class="section-title">{{ movieSectionTitle }}</h1>
      <!-- PREV BUTTON -->
      <div id="movies-row" class="row">
        <div class="slider-commands prev" @click="moviesGoPrev('movies-row')"> <i class="fas fa-chevron-left"></i> </div>
        <!-- CARDS -->
        <card-box
          v-for="(card, i) in moviesCards"
          :key="i"
          :card="card"
          :name="card.title"
          :originalName="card.original_title"
        />
        <!-- NEXT BUTTON -->
        <div class="slider-commands next" @click="moviesGoNext('movies-row')"> <i class="fas fa-chevron-right"></i> </div>
      </div>
    </div>

    <!-- TV SERIES -->
    <div id="tv-series" class="container-fluid">
      <h1 class="section-title">{{ tvSEriesSectionTitle }}</h1>
      <div id="tv-series-row" class="row">
        <!-- PREV BUTTON -->
        <div class="slider-commands prev" @click="seriesGoPrev('tv-series-row')"> <i class="fas fa-chevron-left"></i> </div>
        <!-- CARDS -->
        <card-box
          v-for="(card, i) in seriesCards"
          :key="i"
          :card="card"
          :name="card.name"
          :originalName="card.original_name"
        />
        <!-- NEXT BUTTON -->
        <div class="slider-commands next" @click="seriesGoNext('tv-series-row')"> <i class="fas fa-chevron-right"></i> </div>
      </div>
    </div>
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
@import '@/style/variables.scss';

main {
  padding-top: 100px;
}
.container-fluid {
  margin: 120px 0;
  .row {
    flex-wrap: nowrap;
    overflow-x: hidden;
    scroll-behavior: smooth;
    position: relative;
    .slider-commands{
      background: rgba(0, 0, 0, .2);
      font-size: 50px;
      color: $secondary-text-color;
      width: 50px;
      height: 467;
      display: flex;
      align-items: center;
      justify-content: center;
      position: sticky;
      z-index: 1;
      cursor: pointer;
      transition: all .5s;
      &:hover{
      background: rgba(0, 0, 0, .8);
      color: $primary-text-color;
      }
    }
    .slider-commands.next{
      right: 0;
    }
    .slider-commands.prev{
      left: 0;
      margin-right: -50px;
    }
  }
}
</style>
