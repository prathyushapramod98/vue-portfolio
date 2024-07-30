<template>
  <metainfo> </metainfo>

  <div
    class="scrollspy-example"
    data-bs-offset="0"
    data-bs-spy="scroll"
    data-bs-target="#main-nav"
    tabindex="0"
  >
    <!-- Render active component contents with vue transition -->
    <transition name="fade" mode="out-in">
      <router-view />
    </transition>
    <!-- Menu -->
    <MenuVue :links="links" :class="[isDarkMode ? 'text-black' : 'text-white']">
      <template v-slot:icon>
        <font-awesome-icon
          @click="toggleDarkMode"
          :icon="['fas', isDarkMode ? 'moon' : 'sun']"
          class="toggle-dark-mode-icon"
        />
      </template>
      <template v-slot:name>
        <span id="hero" class="p-2"> Prathyusha</span>
      </template>
    </MenuVue>
  </div>
</template>
<script>
import { useMeta } from "vue-meta";
import MenuVue from "@/components/shared/AppMenu.vue";

export default {
  data: () => {
    return {
      isDarkMode: false,
      delay: 100,
      webTitle: "Prathyusha - Frondend Developer",
      links: [
        {
          name: "Home",
          url: "#hero",
        },
        {
          name: "About",
          url: "#about",
        },
        {
          name: "Skills",
          url: "#skills",
        },
        {
          name: "Experience",
          url: "#edu-exp",
        },
      ],
    };
  },
  setup() {
    useMeta({
      title: "Prathyusha - Frontend Developer",
      description: "Just a guy with passion for coding",
      htmlAttrs: {
        lang: "en",
        amp: true,
      },
      twitter: {
        title: "Prathyusha - Frondend Developer",
        description: "Just a guy with passion for coding",
        card: "summary_large_image",
        image: "https://rusetskii.dev" + require(`@/assets/images/preview.jpg`),
      },
      og: {
        title: "Prathyusha - Frondend Developer",
        description: "Just a guy with passion for coding",
        type: "website",
        site_name: "Prathyusha - Frondend Developer",
      },
      meta: [
        {
          name: "keywords",
          content:
            "software developer, vue.js developer, frontend developer, developer portfolio",
        },
        {
          name: "author",
          content: "Prathyusha",
        },
      ],
      link: [
        {
          rel: "icon",
          href: require(`@/assets/images/favicon.png`),
        },
      ],
    });
  },
  mounted() {
    const savedDarkMode = localStorage.getItem("darkMode");
    if (savedDarkMode) {
      this.isDarkMode = savedDarkMode === "true";
      document.documentElement.classList.toggle("dark", this.isDarkMode);
    }
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode;
      localStorage.setItem("darkMode", this.isDarkMode);
      document.documentElement.classList.toggle("dark", this.isDarkMode);
    },
  },
  components: {
    MenuVue,
  },
};
</script>
<style lang="scss">
html {
  scroll-behavior: smooth;
}

body {
  position: relative;
  font-family: $default-family;
  font-size: $default-font-size;
}

::-webkit-scrollbar {
  width: 9px;
}

::-webkit-scrollbar-thumb {
  background: #363636;
}

::-webkit-scrollbar-track {
  background: #fff;
}

.btn {
  border-width: 1px;
  cursor: pointer;
  justify-content: center;
  padding: calc(0.5em - 1px) 1em;
  text-align: center;
  white-space: nowrap;
  -webkit-appearance: none;
  align-items: center;
  border-radius: 4px;
  box-shadow: none;
  display: inline-flex;
  font-size: 1rem;
  height: 2.5em;
  line-height: 1.5;
  position: relative;
  vertical-align: top;
}

.btn-primary {
  color: white;
}

a,
a:active,
a:visited {
  text-decoration: none !important;
}

body {
  background-color: white;
  color: black;
}

.dark body {
  background-color: #1a202c;
  color: white;
}
</style>
