<template>
  <div class="container">
    <div class="hijo">
      <img :src="img" alt="" />
    </div>
    <p>{{ texto }}</p>
  </div>
</template>

<script>
export default {
  props: {
    img: {
      type: String,
      required: true,

    },
    texto: {
      type: String,
      required: true,
    },
  },
};
</script>

<style >
img {
  width: 250px;
  height: 250px;
}

</style>