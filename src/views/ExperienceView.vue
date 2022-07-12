<template>
  <section>
    <h1>{{ experience.name }}</h1>
    <img :src="`/images/${experience.image}`" :alt="experience.name" />
    <p>
      {{ experience.description }}
    </p>
  </section>
</template>

<script>
import sourceData from "@/data.json";
export default {
  name: "ExperienceView",
  props: {
    id: {
      type: Number,
      required: true,
    },
    experienceSlug: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      destinations: sourceData.destinations,
    };
  },
  computed: {
    destination() {
      return sourceData.destinations.find(
        (destination) => destination.id === this.id
      );
    },
    experience() {
      return this.destination.experiences.find(
        (experience) => experience.slug === this.experienceSlug
      );
    },
  },
};
</script>
