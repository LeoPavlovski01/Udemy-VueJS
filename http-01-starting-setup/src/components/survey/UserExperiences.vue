<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button>Load Submitted Experiences</base-button>
      </div>
      <ul>
        <survey-result
          v-for="result in results"
          :key="result.id"
          :name="result.name"
          :rating="result.rating"
        ></survey-result>
      </ul>
    </base-card>
  </section>
  <my-learning-survey @submit-survey="submitData"></my-learning-survey>
  <my-user-experiences :results="surveyResults"></my-user-experiences>
</template>

<script>
import SurveyResult from './SurveyResult.vue';
import MyLearningSurvey from './MyLearningSurvey.vue'
import MyUserExperiences from './MyUserExperiences.vue'

export default {
  props: ['results'],
  data(){
    return{
      surveyResults:[],
    }
  },
  components: {
    MyUserExperiences,
    MyLearningSurvey,
    SurveyResult,
  },
  methods:{
    submitData(submittedForm){
      const data = {
        name:submittedForm.username,
        experience:submittedForm.experience,
      }
      this.surveyResults.push(data);
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>