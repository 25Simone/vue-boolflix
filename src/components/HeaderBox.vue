<template>
    <header class="container-fluid">
        <div class="logo">
            <img class="img-fluid" src="@/assets/boolflix-logo.png" alt="logo boolflix">
        </div>
        <div class="input-area">
            <input
            type="text"
            placeholder="Search"
            v-model="searchedContent">
            <div class='button'>Search</div>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            searchedContent: '',
        }
    },
}
</script>

<style lang="scss" scoped>
header{
    background: #1b1b1b;
    padding: 15px 25px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .logo{
        width: 150px;
    }
    .input-area{
        display: flex;
        align-items: center;
    }
}
</style>