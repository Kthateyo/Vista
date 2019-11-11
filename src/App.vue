<template>
  <div id="app">

    <Background/>

  </div>
</template>

<script>
import Background from './components/Background.vue';

export default {
  name: 'app',
  components: {
    Background,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
