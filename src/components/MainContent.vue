<template>
    <main>
        <!-- MOVIES -->
        <div class="container-fluid">
            <h1 class="section-title">MOVIES</h1>
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
            <h1 class="section-title">TV SERIES</h1>
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
  }
    
}
</script>

<style lang="scss" scoped>
.container-fluid{
    margin: 50px 0;
    .row{
        flex-wrap: nowrap;
        overflow-x: auto;
    }
}
</style>