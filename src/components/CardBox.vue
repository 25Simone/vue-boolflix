<template>
    <div class="card col-2">
        <!-- CARD IMAGE -->
        <div class="card-img">
            <img class="img-fluid" :src="`https://image.tmdb.org/t/p/original${card.poster_path}`">
        </div>
        <div class="card-data">
            <ul>
                <li><strong>Titolo:</strong> {{card.title}}</li>
                <li><strong>Titolo originale:</strong> {{card.original_title}}</li>
                <li><strong>Voto:</strong> {{card.vote_average}}</li>
                <li><strong>Overview:</strong> {{card.overview}}</li>
            </ul>
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
    padding: 0;
    margin: 10px;
    border: 1px solid #1b1b1b;
    cursor: pointer;
    .card-img{
        width: 100%;
        height: 100%;
        img{
            height: 100%;
        }
    }
    .card-data{
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, .8);
        padding: 20px 10px 0 10px;
        position: absolute;
        top: 0;
        left: 0;
        display: none;
        overflow-y: auto;
        ul{
            // reset
            margin: 0;
            padding: 0;
            font-size: 12px;
            list-style: none;
            color: #fff;
        }
    }
    // hover effect
    &:hover .card-data{
        display: block;
    }
}

</style>