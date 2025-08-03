<template>
  <div>
    <li>
      <p>
        <span class="highlight">{{ name }}</span> rated the learning experience
        <span :class="ratingClass">{{ rating }}</span>
      </p>
      <div>
        <i
          @click="deleteExperience"
          style="cursor: pointer; color: red; font-size: 20px"
          class="mdi mdi-delete"
        ></i>
      </div>
    </li>
  </div>
</template>

<script>
export default {
  data() {
    return {
      error: null,
      deleted: false,
    };
  },
  props: ['name', 'rating', 'results', 'id'],
  computed: {
    ratingClass() {
      return 'highlight rating--' + this.rating;
    },
  },
  methods: {
    //   Handle delete
    deleteExperience() {
      this.error = null;
      fetch(
        `https://vue-http-demo-a77f1-default-rtdb.firebaseio.com/surveys/${this.id}.json`,
        {
          method: 'DELETE',
          headers: {
            'Content-Type': 'application/json',
          },
        }
      )
        .then((response) => {
          if (response.ok) {
            this.error = false;
            this.deleted = true;
            // this.getExperiences();
            this.$emit('deleted');
            return response.json();
          } else {
            this.error = true;
            this.deleted = false;
            //  400,500 handling
            throw new Error('Failed to delete item.');
          }
        })
        .catch((error) => {
          this.deleted = false;
          this.error = true;
          this.error = error.message;
        });
    },
  },
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

h3,
p {
  font-size: 1rem;
  margin: 0.5rem 0;
}

.highlight {
  font-weight: bold;
}

.rating--poor {
  color: #b80056;
}

.rating--average {
  color: #330075;
}

.rating--great {
  color: #008327;
}
</style>
