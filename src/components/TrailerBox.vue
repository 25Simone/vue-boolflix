<template>
    <div class="container-fluid trailer">
        <!-- TRAILER VIDEO -->
        <video ref="firstMovieTrailer" width="100%" height="100%" autoplay muted loop>
            <source src="@/assets/NWH-trailer-ita.mp4" type="video/mp4">
        </video>
        <!-- VIDEO COMMANDS -->
        <div class="video-commands trailer-el">
            <!-- PLAY / PAUSE -->
            <span id="play-command" @click="playCommands">
                <i v-if="!isPlaying" class="far fa-play-circle"></i>
                <i v-else class="far fa-pause-circle"></i>
            </span>
            <!-- MUTE / UNMUTE -->
            <span id="mute-command" @click="muteCommands">
                <i v-if="isMute" class="fas fa-volume-mute"></i>
                <i v-else class="fas fa-volume-up"></i>
            </span>
        </div>
        <!-- TRAILER MESSAGE -->
        <div id="trailer-message" class="trailer-el">Scelto per te oggi</div>
        <!-- LOGO MOVIE TRAILER -->
        <img class="trailer-el" src="@/assets/NWH-logo.png" alt="Spiderman no way home logo">
        <!-- STATIC PLAY BUTTON -->
        <div id="play-movie-trailer" class="button trailer-el">
            <a href="#movies"> <i class="fas fa-play"></i> Riproduci</a>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            isPlaying: true,
            isMute: true,
        }
    },
    methods: {
        playCommands(){
            if(this.isPlaying){
                this.$refs.firstMovieTrailer.pause();
                this.isPlaying = false;
            } else {
                this.$refs.firstMovieTrailer.play();
                this.isPlaying = true;
            }
            console.log(this.isPlaying) //DEBUG
        },
        muteCommands(){
            const video = this.$refs.firstMovieTrailer;
            video.muted = !video.muted;
            this.isMute = !this.isMute;
        }
    }
}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';

.trailer-el{
    position: absolute;
}

.container-fluid.trailer{
    height: 90vh;
    position: relative;
    padding-top: 70px;
    video{
        object-fit: cover;
    }
    .video-commands{
        color: $primary-text-color;
        font-size: 70px;
        right: 50px;
        bottom: 10%;
        >span{
            margin: 0 30px;
        }
    }
    #trailer-message{
        font-size: 55px;
        font-weight: 500;
        color: $primary-text-color;
        top: 9%;
        left: 3%;
    }
    img{
        width: 500px;
        bottom: 30%;
        left: 3%;
    }
    #play-movie-trailer.button{
        border-radius: 10px;
        padding: 10px 20px;
        background: $primary-text-color;
        color: #000;
        font-size: 25px;
        left: 3%;
        bottom: 10%;
        a{
            text-decoration: none;
            color: #000;
        }
    }
}
</style>