<template>
    <!-- CARD -->
    <div class="card col-2">
        <!-- CARD IMAGE -->
        <div class="card-img">
            <img v-if="card.poster_path != null" class="img-fluid" :src="`https://image.tmdb.org/t/p/original${card.poster_path}`">
            <img v-else class="img-fluid" src="https://www.sirem.org/wp-content/uploads/2021/04/no-image.jpg" alt="not found placeholder">
        </div>
        <!-- CARD DATA -->
        <div class="card-data">
            <ul>
                <!-- TITLES -->
                <li><strong>Titolo:</strong> {{name}}</li>
                <li><strong>Titolo originale:</strong> {{originalName}}</li>
                <!-- LANGUAGE -->
                <li>
                    <strong>Lingua originale:</strong>
                    <linguages-flags :card="card"/>
                <li>
                <!-- VOTE -->
                <li>
                    <strong>Voto: </strong>
                    <!-- STARS -->
                    <stars-rateing :rate="card.vote_average" />
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import StarsRateing from './StarsRateing.vue';
import LinguagesFlags from './LinguagesFlags.vue'

export default {
    components: {
        StarsRateing,
        LinguagesFlags,
    },
    props: {
        card: Object,
        name: String,
        originalName: String,
    },
    methods: {
        
    }
}
</script>

<style lang="scss" scoped>
.card{
    padding: 0;
    border-left: 2px solid #1b1b1b;
    border-right: 2px solid #1b1b1b;
    background: transparent;
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
            font-size: 15px;
            list-style: none;
            color: #fff;
            li{
                margin-top: 10px;
            }
        }
        .flag{
            margin-left: 10px;
        }
    }
    // hover effect
    &:hover .card-data{
        display: block;
    }
}

</style>