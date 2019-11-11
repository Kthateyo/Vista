<template>
  <div class="background"></div>
</template>

<script>
export default {
  name: 'Background',
};
</script>

<style>
.background {
  width: 100%;
  height: 100vh;

  position: fixed;
  z-index: -1;
  background: url('https://images.pexels.com/photos/1252869/pexels-photo-1252869.jpeg?auto=compress&cs=tinysrgb&dpr=3&h=750&w=1260') no-repeat;
  background-size: cover;
}
</style>
