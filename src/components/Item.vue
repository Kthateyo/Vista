<template>
  <a :href="href" target="_blank" :style="`background-image: url(${photo})`" class="item"></a>
</template>

<script>
export default {
  name: 'Item',
  props: {
    photo: {
      type: String,
      required: true,
    },
    href: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
.item {
  width: 280px;
  height: 280px;
  margin: 20px;

  background: center no-repeat;
  background-size: cover;

  @media (max-width: 740px) {
    width: 190px;
    height: 190px;
  }
  @media (max-width: 450px) {
    width: 360px;
    height: 360px;
    margin: 10px;
    margin-bottom: 50px;
  }

}

.item:focus {
  cursor: pointer;
}
</style>
