<template>
  <div id="app" :class="[{flexStart: step === 1}, 'wrapper']">

    <transition name="slide">
      <div class="logo" v-if="step === 1">VISTA</div>
    </transition>

    <transition name="fade">
      <Background v-if="step === 0"/>
    </transition>

      <Claim v-if="step === 0"/>

    <transition name="fade">
      <SearchInput @onSearch="handleInput($event)" :dark="step === 1"/>
    </transition>

    <div class="results" >
      <div v-for="result in results" :key="result.id"
      :style="`background-image: url(${result.webformatURL})`" class="item"></div>
    </div>

  </div>
</template>

<script>
import axios from 'axios';
import Background from './components/Background.vue';
import Claim from './components/Claim.vue';
import SearchInput from './components/SearchInput.vue';

const API = 'https://pixabay.com/api/?key=14238039-34193333c5f4e49e957b06950&per_page=100&q=';

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
          this.loading = false;
          this.step = 1;
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
  padding: 40px;

  position: relative;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &.flexStart {
    justify-content: flex-start
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}
.fade-enter, .fade-leave-to
/* .component-fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.slide-enter-active, .slide-leave-active {
  transition: margin-top .3s ease;
}
.slide-enter, .slide-leave-to
/* .component-fade-leave-active below version 2.1.8 */ {
  margin-top: -50px;
}

.logo {
  position: absolute;
  top: 20px;
  color: black;
  font-size: 3.5em;
  font-weight: 600;
}

.results {
  margin-top: 50px;
  width: 1000px;

  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;

  color: black;
}

.item {
  width: 280px;
  height: 280px;
  margin: 20px;

  background: center no-repeat;
  background-size: cover;
}
</style>
