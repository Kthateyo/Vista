<template>
  <input type="text" :class="{dark: dark}" v-model="searchContent" @keyup.enter="onSearch"/>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    dark: {
      type: Boolean,
      default: false,
    },
  },
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
    border-bottom: 1px solid rgb(255, 255, 255);
  }

  input:focus {
    box-shadow: 0px 10px 8px -6px rgba(255, 255, 255, 0.6);
  }

  .dark {
    margin-top: 50px;
    border-bottom-color: black;
    color: black;
  }

  .dark:focus {
    box-shadow: 0px 10px 8px -6px rgba(0, 0, 0, 0.4);
  }
</style>
