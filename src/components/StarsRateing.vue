<template>
    <div>
        <span
        class="stars"
        v-for="(star, index) in 5"
        :key="index"
        >
        <!-- FULL STARS -->
        <i v-if="index <= starsRate" class="fas fa-star"></i>
        <!-- EMPTY STARS -->
        <i v-else class="far fa-star"></i>
    </span>
    </div>
</template>

<script>
export default {
    props: {
        rate:Number,
    },
    computed: {
        starsRate(){
            return Math.floor(this.rate / 2);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>