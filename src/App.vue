<template>
  <div id="app">
    <SearchMainPage />
  </div>
</template>

<script>
import SearchMainPage from './components/SearchMainPage.vue';

export default {
  name: 'App',
  components: {
    SearchMainPage,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
