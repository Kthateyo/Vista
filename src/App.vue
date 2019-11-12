<template>
  <div id="app">

    <Background/>
    <Claim/>
  </div>
</template>

<script>
import Background from './components/Background.vue';
import Claim from './components/Claim.vue';

export default {
  name: 'app',
  components: {
    Background,
    Claim,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: azure;
}
</style>
