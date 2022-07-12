<template>
  <div id="nav">
    <AppLink id="logo" to="/">Vue Travel App</AppLink>
    <AppLink
      v-for="destination in destinations"
      :key="destination.id"
      :to="{
        name: 'destination.show',
        params: { id: destination.id, slug: destination.slug },
      }"
    >
      <h4 class="destination-name">{{ destination.name }}</h4>
    </AppLink>
    <AppLink :to="{ name: 'protected' }"> Dashboard </AppLink>
    <AppLink to="https://vueschool.io">Vue School</AppLink>
  </div>
</template>

<script>
import sourceData from "@/data.json";
export default {
  name: "HomeView",
  data() {
    return {
      destinations: sourceData.destinations,
    };
  },
};
</script>

<style lang="css">
#nav .vue-place-active-link {
  color: black;
  border-bottom: 2px solid black;
}
</style>
