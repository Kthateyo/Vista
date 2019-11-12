<template>
  <div :class="[{flexStart: step === 1}, 'wrapper']">

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
@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,500,600&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: 'Montserrat', sans-serif;
  color: white;
}

.wrapper {
  width: 100%;
  height: 100vh;
  padding: 30px;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &.flexStart {
    justify-content: flex-start
  }
}
</style>
