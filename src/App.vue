<template>
  <div id="app">
    <SearchYoutube msg="YouTube動画検索"/>
  </div>
</template>

<script>
import SearchYoutube from './components/SearchYoutube.vue'
export default {
  name: 'app',
  components: {
    SearchYoutube
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
