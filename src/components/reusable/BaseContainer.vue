<template>
  <section class="p-3 p-lg-5">
    <div class="container">
      <div class="row">
        <h2 class="title my-md-5 mb-3 text-center">{{ title }}</h2>
        <slot />
      </div>
    </div>
  </section>
</template>
<script>
export default {
  props: ["title"],
};
</script>
<style lang="scss">
.title {
  color: #be6400;
}
</style>
