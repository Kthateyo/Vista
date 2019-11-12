<template>
  <div id="app">

    <Background v-if="step === 0"/>
    <Claim v-if="step === 0"/>
    <SearchInput @onSearch="handleInput($event)" :dark="step === 1"/>

  </div>
</template>

<script>
import axios from 'axios';
import Background from './components/Background.vue';
import Claim from './components/Claim.vue';
import SearchInput from './components/SearchInput.vue';

const API = 'https://pixabay.com/api/?key=14238039-34193333c5f4e49e957b06950&q=';

export default {
  name: 'app',
  components: {
    Background,
    Claim,
    SearchInput,
  },
  data() {
    return {
      loading: false,
      step: 0,
      results: [],
    };
  },
  methods: {
    handleInput(event) {
      this.loading = true;
      const query = event.replace(' ', '+');
      axios.get(`${API}${query}`)
        .then((response) => {
          this.results = response.data.hits;
        })
        .catch((error) => {
          console.log(error);
        });
    },
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
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: azure;
}
</style>
