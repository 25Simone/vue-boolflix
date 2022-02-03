<template>
    <main>
        <div class="container">
            <!-- CARDS -->
            <div class="row">
                <card-box
                v-for="(card, i) in cards"
                :key="i"
                :card="card"
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
      cards: Array,
  }
    
}
</script>

<style lang="scss" scoped>
</style>