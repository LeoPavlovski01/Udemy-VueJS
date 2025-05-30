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
    <learning-resource class="card-item" :resource="res" v-for="res in resources" :key="res.id"></learning-resource>
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
.card-item{
  margin: 2rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
}
</style>