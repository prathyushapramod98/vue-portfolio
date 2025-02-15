<template>
  <a class="btn mr-md-2" :href="url" role="button" target="_blank"
    ><font-awesome-icon :icon="icon.split(' ')" /><slot></slot
  ></a>
</template>
<script>
export default {
  props: ["url", "icon"],
};
</script>
<style></style>
