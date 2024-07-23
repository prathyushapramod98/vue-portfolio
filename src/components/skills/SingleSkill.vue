<template>
  <div class="col-sm-12 col-md-4 mb-3">
    <div class="text-center">
      <img
        class="mb-3"
        :src="require(`@/assets/images/${skill.image}`)"
        data-aos="fade-up"
        :data-aos-delay="delay"
        data-aos-anchor-placement="top-bottom"
      />
      <h4
        class="tags mb-3 has-text-weight-semibold"
        data-aos="fade-up"
        :data-aos-delay="delay + 200"
        data-aos-anchor-placement="top-bottom"
      >
        <span class="tag" :class="skill.css">
          {{ skill.title }}
        </span>
      </h4>
      <div>
        {{ skill.description }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "SingleSkill",
  props: ["skill"],
  data: () => {
    return {
      delay: 500,
    };
  },
};
</script>
<style scoped>
img {
  width: 128px;
  height: 128px;
}

.tags .tag:not(:last-child) {
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
}

.tag:not(body) {
  align-items: center;
  background-color: #f5f5f5;
  color: #4a4a4a;
  display: inline-flex;
  font-size: 0.75rem;
  height: 2em;
  justify-content: center;
  line-height: 1.5;
  padding-left: 0.75em;
  padding-right: 0.75em;
  white-space: nowrap;
}

span {
  -webkit-transition: 0.1s ease-in;
  -o-transition: 0.1s ease-in;
  transition: 0.1s ease-in;
}

span:hover {
  -webkit-transform: translate3d(0px, -5px, 0px);
  transform: translate3d(0px, -5px, 0px);
}

.vuejs:hover {
  color: #fff;
  background-color: #4fc08d;
}

.nuxtjs:hover {
  color: #fff;
  background-color: #00d1b2;
}

.javascript:hover {
  color: #000;
  background-color: #f7df1e;
}

.bootstrap:hover {
  color: #fff;
  background-color: #7952b3;
}

.css:hover {
  color: #fff;
  background-color: #007396;
}

.html:hover {
  color: #fff;
  background-color: #d14020;
}

.vuetify:hover {
  color: #fff;
  background-color: #18c5ef;
}

.tailwind:hover {
  color: #fff;
  background-color: #0d98ba;
}

.supabase:hover {
  color: #fff;
  background-color: #6db33f;
}
</style>
