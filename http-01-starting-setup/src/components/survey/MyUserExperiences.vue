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
<!--  emit the data from the survey , store it in a array.-->
  <learning-survey-new @submit-survey="submitData"></learning-survey-new>
  <user-experiences-new :results="sData"></user-experiences-new>
</template>

<script>
import MyBaseButton from "@/components/survey/MyBaseButton.vue";
import mySurveyResult from "@/components/survey/mySurveyResult.vue";
import LearningSurveyNew from "@/components/survey/LearningSurveyNew.vue"
import UserExperiencesNew from "@/components/survey/UserExperiencesNew.vue"
export default {
  props:['results'],
  name: "MyUserExperiences.vue",
  components: {UserExperiencesNew, LearningSurveyNew, MyBaseButton ,mySurveyResult},
  data(){
    return{
      sData:[],
    }
  },
  methods:{
    submitData(data){
      const surveyData = {
        username:data.username,
        experience:data.experience,
      }
      this.sData.push(surveyData);
    }
  }
}
</script>

<style scoped>

</style>