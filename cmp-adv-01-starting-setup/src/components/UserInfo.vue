<template>
  <section>
    <base-card>
      <template #header>
        <h3>{{ activeUser.name }}</h3>
        <base-badge :type="activeUser.role" :caption="activeUser.role.toUpperCase()"></base-badge>
      </template>
      <template #default>
        <p>{{ activeUser.description }}</p>
      </template>
    </base-card>
  </section>
</template>

<script>
import BaseCard from "@/components/UI/BaseCard.vue";
export default {
  props: ['activeUser'],
  components:{
    BaseCard
  }
};
</script>

<style scoped>

</style>