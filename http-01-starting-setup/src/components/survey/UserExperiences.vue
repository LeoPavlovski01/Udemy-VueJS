<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button @click="getSurveys"
          >Load Submitted Experiences</base-button
        >
      </div>
      <!--      Basic loading-->
      <p v-if="loading">Loading ... please wait</p>
      <!--      If we have an catch error while fetching-->
      <p v-else-if="!loading && errorMessage">{{ errorMessage }}</p>
      <p v-else-if="!loading && (!surveyResults || surveyResults.length === 0)">
        No Stored experiences found. Add some!
      </p>
      <ul v-else>
        <survey-result
          v-for="result in surveyResults"
          :key="result.id"
          :name="result.name"
          :rating="result.rating"
        ></survey-result>
      </ul>
    </base-card>
  </section>
  <!--  <my-learning-survey @submit-survey="submitData"></my-learning-survey>-->
  <!--  <my-user-experiences :results="surveyResults"></my-user-experiences>-->
</template>

<script>
import SurveyResult from './SurveyResult.vue';
// import MyLearningSurvey from './MyLearningSurvey.vue'
// import MyUserExperiences from './MyUserExperiences.vue'

export default {
  data() {
    return {
      surveyResults: [],
      loading: false,
      errorMessage: null,
    };
  },
  mounted() {
    this.getSurveys();
  },
  components: {
    // MyUserExperiences,
    // MyLearningSurvey,
    SurveyResult,
  },
  methods: {
    getSurveys() {
      this.loading = true;
      this.errorMessage = null;
      fetch(
        'https://vue-http-demo-a77f1-default-rtdb.firebaseio.com/surveys.json'
      )
        .then((response) => {
          if (response.ok) {
            return response.json();
          }
          //  Using the arrow functions is better , cuz we cannot access this keywoard out of the scope.
        })
        .then((data) => {
          this.loading = false;
          const results = [];
          // Transforming the objects to an array of objects so we can iterate through them.
          for (const id in data) {
            results.push({
              id: id,
              name: data[id].name,
              rating: data[id].rating,
            });
          }
          this.surveyResults = results;
        })
        .catch(() => {
          this.loading = false;
          this.errorMessage =
            'Failed to fetch the data, please try again later ...';
        });
    },

    // test(){
    //   console.log('test');
    // },
    // submitData(submittedForm){
    //   const data = {
    //     name:submittedForm.username,
    //     experience:submittedForm.experience,
    //   }
    //   this.surveyResults.push(data);
    // }
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
