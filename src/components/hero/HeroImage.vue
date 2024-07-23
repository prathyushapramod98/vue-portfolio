<template>
  <div class="col-10 col-sm-7 col-lg-7">
    <img
      :alt="alt"
      class="image d-block mx-lg-auto img-fluid rounded-full"
      loading="lazy"
      :src="require(`@/assets/images/${src}`)"
    />
  </div>
</template>
<script>
export default {
  props: ["src", "alt"],
};
</script>
<style scoped>
.image {
  height: 90%;
  width: 90vh;
}
</style>
