<template>
  <section>
    <base-card>
      <h2>How was you learning experience?</h2>
      <form @submit.prevent="submitSurvey">
        <div class="form-control">
          <label for="name">Your Name</label>
          <input type="text" id="name" name="name" v-model.trim="enteredName" />
        </div>
        <h3>My learning experience was ...</h3>
        <div class="form-control">
          <input
            type="radio"
            id="rating-poor"
            value="poor"
            name="rating"
            v-model="chosenRating"
          />
          <label for="rating-poor">Poor</label>
        </div>
        <div class="form-control">
          <input
            type="radio"
            id="rating-average"
            value="average"
            name="rating"
            v-model="chosenRating"
          />
          <label for="rating-average">Average</label>
        </div>
        <div class="form-control">
          <input
            type="radio"
            id="rating-great"
            value="great"
            name="rating"
            v-model="chosenRating"
          />
          <label for="rating-great">Great</label>
        </div>
        <p v-if="invalidInput">
          One or more input fields are invalid. Please check your provided data.
        </p>
        <p v-if="error">
          {{ error }}
        </p>
        <div>
          <base-button>Submit</base-button>
        </div>
      </form>
    </base-card>
  </section>
</template>

<script>
export default {
  data() {
    return {
      enteredName: '',
      chosenRating: null,
      invalidInput: false,
      error: null,
    };
  },
  methods: {
    submitSurvey() {
      // Validation
      if (this.enteredName === '' || !this.chosenRating) {
        this.invalidInput = true;
        return;
      }
      this.invalidInput = false;
      this.error = null;
      fetch(
        'https://vue-http-demo-a77f1-default-rtdb.firebaseio.com/surveys.json',
        {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          // When the request is wrong, it will go to the first .then case.
          body: JSON.stringify({
            name: this.enteredName,
            rating: this.chosenRating,
          }),
          //   Status code.
        }
      )
        .then((response) => {
          if (response.ok) {
            return response.json();
          } else {
            // Handling 400 , 500 status code errors.
            throw new Error('Could not save data...');
          }
          // technical errors catch. (endpoint PROBLEMS)
        })
        //   CORS , No connection , DNS failure.
        .catch((error) => {
          // When for example the fetch method is /surveys and not /surveys.json this will end up here, because
          // it's an issue with the url.
          this.error = error.message;
        });

      // this.$emit('survey-submit', {
      //   userName: this.enteredName,
      //   rating: this.chosenRating,
      // });
      this.enteredName = '';
      this.chosenRating = null;
    },
  },
};
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
