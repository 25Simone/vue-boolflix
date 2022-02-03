<template>
    <div class="card col-2">
        <div class="img">
            <img class="img-fluid" :src="`https://image.tmdb.org/t/p/original${card.poster_path}`">
        </div>
        <div class="card-data">

        </div>
    </div>
</template>

<script>
export default {
    props: {
        card: Object,
    }
}
</script>

<style lang="scss" scoped>
.card{
    padding: 20px 10px;
    margin: 10px;
    border: 1px solid #000;
}

</style>