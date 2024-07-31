<template>
  <nav
    :class="[
      'navbar',
      'navbar-expand-lg',
      'fixed-top',
      isDarkMode ? 'navbar-dark bg-orange-500' : 'navbar-light bg-white',
    ]"
    id="main-nav"
  >
    <div class="container">
      <a class="logo navbar-brand d-flex align-items-center" href="#">
        <slot name="name"></slot>
      </a>
      <button
        aria-controls="navbar4"
        aria-expanded="false"
        aria-label="Toggle navigation"
        class="navbar-toggler"
        data-bs-target="#navbar4"
        data-bs-toggle="collapse"
        type="button"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbar4">
        <ul class="navbar-nav ms-auto">
          <li v-for="link in links" :key="link.name" class="nav-item px-lg-2">
            <a class="nav-link" :href="link.url">{{ link.name }}</a>
          </li>
          <li class="nav-item px-lg-2 d-flex align-items-center">
            <slot name="icon"></slot>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  props: {
    links: Array,
    isDarkMode: Boolean,
  },
  name: "AppMenu",
};
</script>
<style lang="scss" scoped>
* {
  font-weight: 600;
}

.nav-link.active {
  border-bottom: 2px solid#be6400;
}

.logo {
  font-size: 20px;
  display: flex;
  align-items: center;
  text-decoration: none;
  font-weight: bold;
  font-display: auto;
  font-family: "Bungee Spice", sans-serif;
}
</style>
