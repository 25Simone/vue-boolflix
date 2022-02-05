<template>
    <main>
        <!-- MOVIES -->
        <div class="container-fluid">
            <h1 class="section-title">{{movieSectionTitle}}</h1>
            <!-- CARDS -->
            <div class="row">
                <card-box
                v-for="(card, i) in moviesCards"
                :key="i"
                :card="card"
                :name="card.title"
                :originalName="card.original_title"
                />
            </div>
        </div>

        <!-- TV SERIES -->
        <div class="container-fluid">
            <h1 class="section-title">{{tvSEriesSectionTitle}}</h1>
            <!-- CARDS -->
            <div class="row">
                <card-box
                v-for="(card, i) in seriesCards"
                :key="i"
                :card="card"
                :name="card.name"
                :originalName="card.original_name"
                />
            </div>
        </div>
    </main>
</template>

<script>
import CardBox from './CardBox.vue'
export default {
  components: {
      CardBox,
  },
  props: {
      moviesCards: Array,
      seriesCards: Array,
      movieSectionTitle: String,
      tvSEriesSectionTitle: String,
  }
    
}
</script>

<style lang="scss" scoped>
main{
    padding-top: 100px;
}
.container-fluid{
    margin: 50px 0;
    .row{
        flex-wrap: nowrap;
        overflow-x: auto;
    }
}
</style>