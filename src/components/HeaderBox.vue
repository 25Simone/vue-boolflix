<template>
  <header class="container-fluid">
    <div class="header-content">
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
        <nav>
          <ul>
            <li> <a href="/">Home</a></li>
            <li> <a href="#tv-series">TvSeries</a></li>
            <li> <a href="#movies">Movies</a></li>
            <li> <a href="/">La mia lista</a></li>
          </ul>
        </nav>
      </div>
      <!-- INPUT AREA -->
      <div class="input-area">
        <input
          type="text"
          placeholder="Search"
          v-model="keywordSearch"
          @keyup="$emit('search', keywordSearch)"
        />
        <div class="button" @click="$emit('search', keywordSearch)"><i class="fas fa-search"></i></div>
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
@import '@/style/variables.scss';

header {
  background: #1b1b1b;
  position: fixed;
  top: 0;
  z-index: 5;
  .header-content{
    padding: 15px 25px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    >div{
      display: flex;
      align-items: center;
    }
  }
  .logo {
    width: 150px;
  }
  .input-area {
    display: flex;
    align-items: center;
    input{
      background: transparent;
      border: none;
      color: $primary-text-color;
    }
  }
  nav{
    ul{
      display: flex;
      align-items: center;
      li{
        padding: 0 20px;
        a{
          color: $secondary-text-color;
          text-decoration: none;
          &:hover{
            color: $primary-text-color;
          }
        }
      }
    }
  }
}
</style>
