<template>
<div>
  <p>{{data.username}} Has Rated
    <span :class="customClass">{{data.experience}}</span>
  </p>
</div>
</template>

<script>


export default {
  props:['data'],
  name: "StoredResultsNew.vue",
  computed:{
    customClass(){
      return 'highlighted experience--' + this.data.experience
    }
  }
}
</script>

<style scoped>
.highlighted{
  font-weight:bold;
}
.experience--poor{
  color:red;
}
.experience--average{
  color:blue;
}
.experience--great{
  color:green;
}
</style>