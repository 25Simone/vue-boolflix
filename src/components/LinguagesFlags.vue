<template>
    <div>
        <span v-if="card.original_language == null">Non pervenuta</span>
        <img class="flag" v-else :src="languagesflags(card.original_language)" alt="languages flag">
    </div>
</template>

<script>
export default {
    props:{
        card: Object,
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
div{
    display: inline-block;
    margin-left: 10px;
}
</style>