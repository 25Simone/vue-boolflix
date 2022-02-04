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
                    <span v-if="card.original_language == null">Non pervenuta</span>
                    <img class="flag" v-else :src="languagesflags(card.original_language)" alt="languages flag">
                <li>
                <!-- VOTE -->
                <li>
                    <strong>Voto: </strong>
                    <!-- STARS -->
                    <span
                    class="stars"
                    v-for="(star, index) in 5"
                    :key="index"
                    >
                        <!-- FULL STARS -->
                        <i v-if="index <= Math.floor(card.vote_average / 2)" class="fas fa-star"></i>
                        <!-- EMPTY STARS -->
                        <i v-else class="far fa-star"></i>
                    </span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        card: Object,
        name:String,
        originalName:String,
    },
    methods: {
        // LANGUAGE FLAG PATH FUNCTION
        languagesflags(language){
            return "/flags/" + language + ".png";
        }
    }
}
</script>

<style lang="scss" scoped>
.card{
    padding: 0;
    border: 2px solid #1b1b1b;
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