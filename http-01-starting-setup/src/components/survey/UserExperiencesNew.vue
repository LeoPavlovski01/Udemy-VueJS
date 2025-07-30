<template>
<div>
  <base-card>
  <h2>Submitted Experiences</h2>
<!--    Showing all of the users and their experiences.-->
    <StoredResultsNew
    v-for="(result,index) in results"
    :key="index"
    :data="result"
    >
    </StoredResultsNew>
    <base-button>Load Submitted Experiences</base-button>
  </base-card>
</div>
</template>

<script>
import StoredResultsNew from "@/components/survey/StoredResultsNew.vue"
import BaseButton from "@/components/UI/BaseButton.vue";
export default {
  name: "UserExperiencesNew.vue",
  components: {BaseButton, StoredResultsNew},
  props:['results'],
}
</script>

<style scoped>

</style>