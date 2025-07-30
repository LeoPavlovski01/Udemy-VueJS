<template>
<div>
  <base-card>
    <h2>How was your learning experience?</h2>
    <form @submit.prevent="submitForm">
      <div class="form-control">
        <span>Your Name</span>
        <input type="text" v-model.trim="userName">
      </div>
      <h3>My learning experience was ... </h3>
        <div class="form-control">
          <input type="radio" value="poor" v-model="experience">
          <label>Poor</label>
          <div class="form-control" >
          <input type="radio" value="average"  v-model="experience">
          <label>Average</label>
        </div>
        <div class="form-control">
          <input type="radio" value="great"  v-model="experience">
          <label>Great</label>
        </div>
          <p v-if="error">Username or Experience is empty.</p>
      </div>
      <base-button>Submit</base-button>
    </form>

  </base-card>
</div>
</template>


<script>
export default {
  name: "LearningSurveyNew.vue",
  data(){
    return{
      userName:'',
      experience:null,
      error:false,
    }
  },
  methods:{
  //   Validation checks
    submitForm(){
      if(!this.userName || !this.experience){
        this.error = true;
        return;
      }
      this.error = false;
      this.$emit('submit-survey', {
        username:this.userName,
        experience:this.experience
      })
      this.userName = '';
      this.experience = null;
    }
  }
}
</script>

<style scoped>
.form-control {
  margin: 0.5rem 0;
}

input[type='text'] {
  display: block;
  width: 20rem;
  margin-top: 0.5rem;
}
</style>