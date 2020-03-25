<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/live">Live</router-link>
    </div>
    <router-view/>
    <footer class="footer">
      <div class="container">
        &copy; 2019-2020 NailToday v2.0 - 4ая попытка
      </div>
    </footer>
  </div>
</template>

<style lang="sass">
  @import 'style/app.sass'
</style>

<style lang="scss">
  #nav {
    padding: 30px;

    a {
      font-weight: bold;
      color: #2c3e50;

      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }
</style>
