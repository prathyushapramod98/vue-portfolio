<template>
  <!-- Menu -->
  <MenuVue :links="links">
    <button @click="toggleDarkMode" class="cursor-pointer w-10 h-10">
      <i :class="`fa fa-${isDarkMode ? 'sun' : 'moon'}`"></i>
    </button>
    <span id="hero"> Prathyusha</span></MenuVue
  >
  <HeroSection id="hero" pic="header.png">
    <template v-slot:welcome
      >Hi, it's me <span class="name">PRATHYUSHA</span><br />
      <h2>Frontend Developer</h2>
    </template>

    <template v-slot:buttons>
      <simple-button
        class="btn-primary text-white"
        url="https://linkedin.com/in/prathyusha-pramod"
        icon="fab linkedin-in"
        >Hire me!</simple-button
      >
      <simple-button
        class="btn-outline-secondary"
        url="mailto:prathyushapachu985@gmail.com"
        icon="fa-regular fa-file-lines"
        >Contact me</simple-button
      >
      <simple-button
        class="btn-primary text-white"
        icon="fa-regular fa-file-pdf"
      >
        <a
          download="Prathyusha-Resume.pdf"
          href="/files/Prathyusha-Resume.pdf"
          class="flex justify-center items-center w-36 sm:w-48 mt-12 mb-6 sm:mb-0 text-lg py-2.5 sm:py-3 text-white duration-500"
          aria-label="Download Resume"
        >
          <i
            data-feather="arrow-down-circle"
            class="ml-0 sm:ml-1 mr-2 sm:mr-3 w-5 sm:w-6 duration-100"
          ></i>
          <span class="text-sm sm:text-lg font-general-medium duration-100"
            >Download CV</span
          ></a
        ></simple-button
      >
    </template>
  </HeroSection>
  <SkillsGrid id="skills" :skills="skills" />
  <ExperienceTable id="edu-exp" :experience="experience" />
  <FooterVue :links="socials" :copyright="copyright" />
</template>
<script>
import MenuVue from "@/components/shared/AppMenu.vue";
import FooterVue from "@/components/shared/AppFooter.vue";
import HeroSection from "@/components/hero/HeroSection.vue";
import SkillsGrid from "@/components/skills/SkillsGrid.vue";
import ExperienceTable from "@/components/experience/ExperienceTable.vue";

// data to fill components
import skills from "@/data/skills";
import experience from "@/data/experience";
import SimpleButton from "@/components/reusable/SimpleButton.vue";

export default {
  name: "HomeView",
  data: () => {
    return {
      isDarkMode: false,
      delay: 100,
      links: [
        {
          name: "Home",
          url: "#hero",
        },
        {
          name: "About",
          url: "#hero",
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
      skills,
      experience,
      socials: [
        {
          id: 1,
          icon: "fab linkedin-in",
          url: "https://linkedin.com/in/prathyusha-pramod",
        },
        {
          id: 2,
          icon: "fab github",
          url: "https://github.com/prathyushapramod98",
        },
      ],
      copyright: "prathyusha",
    };
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
    FooterVue,
    HeroSection,
    SkillsGrid,
    ExperienceTable,
    SimpleButton,
  },
};
</script>
<style lang="scss" scoped>
.prim {
  color: $primary;
}
.name {
  font-family: "Archivo Black", sans-serif;
}
</style>
