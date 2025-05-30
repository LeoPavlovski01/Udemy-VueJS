<template>
<li>
  <BaseCard>
    <template #header>
      <div style="display:flex; align-content: center; justify-content: space-between">
        <h3>{{resource.title}}</h3>
        <button>Delete</button>
      </div>
    </template>
    <template #description>
      <p>{{resource.description}}</p>
    </template>
    <template #link>
      <a :href="resource.link">View Resource</a>
    </template>
  </BaseCard>

</li>
</template>
<script>
import BaseCard from "@/components/UI/BaseCard.vue";
export default {
  props:['resource'],
  components:{
    BaseCard
  }
}
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>