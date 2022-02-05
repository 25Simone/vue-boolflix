<template>
  <header class="container-fluid">
    <div>
      <div>
        <!-- LOGO -->
        <div class="logo">
          <img
            class="img-fluid"
            src="@/assets/boolflix-logo.png"
            alt="logo boolflix"
          />
        </div>
        <!-- NAVBAR -->
        <!-- to-do -->
      </div>
      <!-- INPUT AREA -->
      <div class="input-area">
        <input
          type="text"
          placeholder="Search"
          v-model="keywordSearch"
          @keyup="$emit('search', keywordSearch)"
        />
        <div class="button" @click="$emit('search', keywordSearch)">Search</div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      keywordSearch: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  background: #1b1b1b;
  position: fixed;
  top: 0;
  z-index: 1;
  >div{
    padding: 15px 25px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .logo {
    width: 150px;
  }
  .input-area {
    display: flex;
    align-items: center;
  }
}
</style>
