<template>
<div>
<p>{{name}} has the experience <span :class="ratingText">{{experience}}</span></p>
</div>
</template>

<script>
export default {
  props:['name','experience'],
  name: "mySurveyResult.vue",
  computed:{
    ratingText(){
      return 'highlight rating--' + this.experience;
    }
  }
}
</script>

<style scoped>
.highlight{
  font-weight:bold;
}
.rating--poor{
  color:red;
}
.rating--average{
  color:blue;
}
.rating--great{
  color:green
}
</style>