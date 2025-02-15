<template>
  <div>
    <HeroSection class="hero" pic="3d.png">
      <template v-slot:welcome>
        <div ref="welcomeText">
          Hi, It's Me <span class="name">PRATHYUSHA</span><br />
          <h2 class="designation">Frontend Developer</h2>
        </div>
      </template>
      <template v-slot:buttons>
        <simple-button
          class="btn-outline-secondary"
          url="https://linkedin.com/in/prathyusha-pramod"
          icon="fab fa-linkedin-in"
        />

        <simple-button
          class="btn-outline-secondary"
          url="mailto:prathyushapachu985@gmail.com"
          icon="fas envelope"
        />

        <simple-button
          class="btn-outline-secondary"
          icon="fab fa-github"
          url="https://github.com/prathyushapramod98"
        />

        <simple-button
          class="btn-outline-secondary"
          icon="fas download"
          title="Download CV"
        >
          <a
            download="Prathyusha.pdf"
            href="/files/Prathyusha.pdf"
            class="flex justify-center items-center w-36 sm:w-48 mt-12 mb-6 sm:mb-0 text-lg py-2.5 sm:py-3 text-white duration-500"
            aria-label="Download Resume"
          >
            <!-- <span class="text-sm sm:text-lg font-general-medium duration-100"
              >Download CV</span
            > -->
          </a>
        </simple-button>
      </template>
    </HeroSection>
    <div id="about" class="scroll-trigger">
      <AboutMe />
    </div>
    <div id="skills" class="scroll-trigger">
      <SkillsGrid :skills="skills" />
    </div>
    <div id="edu-exp" class="scroll-trigger">
      <ExperienceTable :experience="experience" />
    </div>
    <FooterVue :links="socials" :copyright="copyright" />
  </div>
</template>

<script>
import { gsap } from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import FooterVue from "@/components/shared/AppFooter.vue";
import HeroSection from "@/components/hero/HeroSection.vue";
import AboutMe from "@/components/about/AboutMe.vue";
import SkillsGrid from "@/components/skills/SkillsGrid.vue";
import ExperienceTable from "@/components/experience/ExperienceTable.vue";
import SimpleButton from "@/components/reusable/SimpleButton.vue";

// data to fill components
import skills from "@/data/skills";
import experience from "@/data/experience";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "HomeView",
  data: () => {
    return {
      skills,
      experience,
      socials: [
        {
          id: 1,
          icon: "fab fa-linkedin-in",
          url: "https://linkedin.com/in/prathyusha-pramod",
        },
        {
          id: 2,
          icon: "fab fa-github",
          url: "https://github.com/prathyushapramod98",
        },
      ],
      copyright: "prathyusha",
    };
  },
  components: {
    FooterVue,
    HeroSection,
    AboutMe,
    SkillsGrid,
    ExperienceTable,
    SimpleButton,
  },
  mounted() {
    // Animation for welcome text
    gsap.from(this.$refs.welcomeText, {
      duration: 1,
      y: 30,
      opacity: 0,
      ease: "power3.out",
    });

    // Scroll animations for sections
    gsap.utils.toArray(".scroll-trigger").forEach((element) => {
      gsap.from(element, {
        scrollTrigger: {
          trigger: element,
          start: "top 30%",
          end: "top 60%",
          toggleActions: "play none none none",
        },
        y: 50,
        opacity: 0,
        duration: 1,
        ease: "power3.out",
      });
    });
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
.designation {
  color: grey;
}
:deep(.dark) .name {
  color: #ffffff;
}
</style>
