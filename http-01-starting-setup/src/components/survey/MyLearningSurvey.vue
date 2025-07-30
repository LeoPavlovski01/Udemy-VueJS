<template>
<base-card>
  <span class="heading">How was your learning experience?</span>
  <form @submit.prevent="submitForm">
    <div class="form-control">
      <p>Your Name</p>
      <input type="text" v-model="userName">
      <h3>My learning experience was ...</h3>
      </div>
<!--      Important-->
    <div class="form-control">
      <input type="radio" id="poor" value="poor"  v-model="experience">
      <label for="poor"> Poor</label>
    </div>

      <div class="form-control">
        <input type="radio" id="average" value="average" v-model="experience">
        <label for="average"> Average</label>
      </div>
      <div class="form-control">
        <input type="radio" id="great" value="great" v-model="experience">
        <label for="great"> Great</label>
      </div>
      <p v-if="invalidInput">One or more input fields are invalid. Please check your provided data.</p>
      <my-base-button>Submit</my-base-button>
  </form>
</base-card>
</template>

<script>
import MyBaseButton from "@/components/survey/MyBaseButton.vue";

export default {
  emits:['submit-survey'],
  name: "MyLearningSurvey.vue",
  components: {MyBaseButton},
  data(){
    return{
    userName:'',
      experience:null,
      invalidInput:false,
    }
  },
  methods:{
    submitForm(){
    //   check for the validation
      if(!this.userName || !this.experience){
       this.invalidInput = true;
       return;
      }

        this.$emit('submit-survey', {
          username:this.userName,
          experience:this.experience
        })

    this.userName = '';
    this.experience = null;
    this.invalidInput = false;
    }
  },
  computed:{

  }
}
</script>

<style scoped>
.heading{
  font-weight:bold;
  font-size:24px;
}
.form-control {
  margin: 0.5rem 0;
}
input[type='text'] {
  display: block;
  width: 20rem;
  margin-top: 0.5rem;
}
</style>