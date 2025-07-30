<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button @click="getSurveys">Load Submitted Experiences</base-button>
      </div>
      <p v-if="loading">Loading ...  please wait</p>
      <p v-else-if="!loading && (!surveyResults || surveyResults.length === 0)">No Stored experiences found. Add some!</p>
      <ul v-else-if="!loading && surveyResults && surveyResults.length > 0">
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
  data(){
    return{
      surveyResults:[],
      loading:false,
    }
  },
  mounted(){
    this.getSurveys();
  },
  components: {
    // MyUserExperiences,
    // MyLearningSurvey,
    SurveyResult,
  },
  methods:{
    getSurveys(){
      this.loading= true;
      fetch('https://vue-http-demo-a77f1-default-rtdb.firebaseio.com/surveys.json').then((response) => {
      if(response.ok){
        return response.json();
      }
     //  Using the arrow functions is better , because of the THIS keywword.

     }).then((data) =>{
       const results = [];
       for(const id in data){
         results.push({
           id:id,
           name:data[id].name,
           rating:data[id].rating,
         })
       }
       this.surveyResults = results;
     }).catch((error)=>{
        console.log('error : ' , error);
      }).finally(()=>{
        this.loading = false;
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