<script>
import MyBaseButton from "@/components/survey/MyBaseButton.vue";
import mySurveyResult from "@/components/survey/mySurveyResult.vue";
export default {
  props:['results'],
  name: "MyUserExperiences.vue",
  components: { MyBaseButton ,mySurveyResult},
  data(){
    return{

    }
  }
}
</script>

<template>
<base-card>
<h2>Submitted Experiences</h2>
  <my-base-button>Load Submitted Experiences</my-base-button>

  <my-survey-result
      v-for="result in results"
      :key="result.id"
      :name="result.name"
      :experience="result.experience"
  >
  </my-survey-result>
</base-card>
</template>

<style scoped>

</style>