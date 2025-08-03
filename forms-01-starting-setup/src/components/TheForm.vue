<template>
  <form @submit.prevent="submitForm">
    <div
      class="form-control"
      :class="{ invalid: validateUserName === 'invalid' }"
    >
      <label for="user-name">Your Name</label>
      <input
        :class="{ invalid: validateUserName === 'invalid' }"
        id="user-name"
        name="user-name"
        type="text"
        v-model.trim="userName"
        @input="validateInput"
      />
      <p v-if="validateUserName === 'invalid'" style="color: red">
        Please Enter A Valid Username!
      </p>
    </div>
    <div
      class="form-control"
      :class="{ invalid: validateUserAge === 'invalid' }"
    >
      <label :class="{ invalid: validateUserAge === 'invalid' }" for="age"
        >Your Age (Years)</label
      >
      <input
        @input="validateInput"
        id="age"
        type="number"
        name="age"
        v-model.trim="userAge"
      />
      <p v-if="validateUserAge === 'invalid'" style="color: red">
        Please Enter A Valid Age!
      </p>
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select v-model="referrer" id="referrer" name="referrer">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input
          @input="validateInput"
          id="interest-news"
          name="interest"
          type="checkbox"
          value="news"
          v-model="interest"
        />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input
          @input="validateInput"
          id="interest-tutorials"
          name="interest"
          type="checkbox"
          value="tutorials"
          v-model="interest"
        />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input
          @input="validateInput"
          id="interest-nothing"
          name="interest"
          type="checkbox"
          value="nothing"
          v-model="interest"
        />
        <label for="interest-nothing">Nothing</label>
      </div>
      <p v-if="selectedInterest === 'invalid'" style="color: red">
        * Please select a checkbox!
      </p>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input
          @input="validateInput"
          id="how-video"
          name="how"
          type="radio"
          v-model="how"
          value="video"
        />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input
          @input="validateInput"
          id="how-blogs"
          name="how"
          type="radio"
          v-model="how"
          value="blogs"
        />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input
          @input="validateInput"
          id="how-other"
          name="how"
          type="radio"
          v-model="how"
          value="other"
        />
        <label for="how-other">Other</label>
      </div>
      <p v-if="selectedLearningOption === 'invalid'" style="color: red">
        * Please select at least one radio button!
      </p>
    </div>
    <div class="form-control">
      <rating-control v-model="rating"></rating-control>
    </div>
    <!--  TODO    Challenge created by me. Having 3 icons ( for example , instagram ,facebook , and twitter
       on click we want to hover the icon to the initial color of the icon. and also send the data which icon has been selected.-->

    <div class="form-control">
      <social-media v-model="socialMedia"></social-media>
    </div>

    <div class="form-control">
      <input
        type="checkbox"
        id="confirm-terms"
        name="confirm-terms"
        v-model="confirm"
      />
      <label for="confirm-terms">Agree to the terms of use?</label>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
import RatingControl from '@/components/RatingControl.vue';
import SocialMedia from '@/components/SocialMedia.vue';

export default {
  components: { SocialMedia, RatingControl },
  data() {
    return {
      userName: '',
      userAge: null,
      referrer: 'wom',
      interest: [],
      rating: null,
      socialMedia: null,
      how: null,
      confirm: false,
      validateUserName: 'pending',
      validateUserAge: 'pending',
      selectedInterest: 'invalid',
      selectedLearningOption: 'invalid',
    };
  },
  methods: {
    submitForm() {
      console.log('confirm', this.confirm);
      this.userName = '';
      this.userAge = null;
      this.referrer = 'wom';
      this.socialMedia = null;
      this.rating = null;
      this.interest = [];
      this.how = null;
      this.confirm = false;
      this.validateUserName = 'pending';
      this.validateUserAge = 'pending';
      this.selectedInterest = 'invalid';
      this.selectedLearningOption = 'invalid';
    },
    validateInput() {
      // Handle userName
      if (this.userName === '') {
        this.validateUserName = 'invalid';
      } else {
        this.validateUserName = 'valid';
      }
      //handle age

      if (!this.userAge || this.userAge > 100 || this.userAge <= 0) {
        this.validateUserAge = 'invalid';
      } else {
        this.validateUserAge = 'valid';
      }
      //  Handle interest checkboxes

      this.selectedInterest = this.interest.length === 0 ? 'invalid' : 'valid';
      this.selectedLearningOption = this.how ? 'valid' : 'invalid';
    },
  },
  computed: {},
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
  width: 100%;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}
.form-control.invalid input {
  border-color: red;
}
.form-control.invalid label {
  color: red;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>
