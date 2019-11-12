<template>
  <input type="text" v-model="searchContent" @keyup.enter="onSearch"/>
</template>

<script>
export default {
  name: 'SearchInput',
  data() {
    return {
      searchContent: '',
    };
  },
  methods: {
    onSearch() {
      this.$emit('onSearch', this.searchContent);
    },
  },
};
</script>

<style>
  input {
    width: 225px;

    display: block;
    margin: auto;

    color: white;
    text-align: center;
    font-size: 1.4em;

    background: none;
    outline: none;
    border: none;
    border-bottom: 3px solid rgba(255, 255, 255, 0.8);
    border-radius: 15%;
  }

  input:focus {
    border-bottom: 3px solid rgba(255, 255, 255, 1.0);
    box-shadow: 0px 10px 8px -4px rgba(255, 255, 255, 0.4);
  }
</style>
