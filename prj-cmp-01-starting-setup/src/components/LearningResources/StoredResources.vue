<script>
import LearningResource from "@/components/LearningResources/LearningResource.vue";

export default {
  name: "StoredResources.vue",
  components: {LearningResource},
  props:['resources']
}
</script>

<template>
  <ul>
    <learning-resource :resource="res" v-for="res in resources" :key="res.id"></learning-resource>
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>