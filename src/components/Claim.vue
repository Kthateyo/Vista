<template>
  <div class="claim">
    <div class="title">VISTA</div>
    <div class="description">
      Our site provides you tons of high quality images of things you like.
    </div>
  </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style scoped>
.claim {
  width: fit-content;

  margin: auto;
  margin-top: 27vh;
  transform: translateY(-50%);

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;


}

.title {
  margin-bottom: 20px;

  font-size: 2.2em;
  font-weight: 600;
}

.description {
  font-size: 1.2em;
  text-align: center;
}

</style>
