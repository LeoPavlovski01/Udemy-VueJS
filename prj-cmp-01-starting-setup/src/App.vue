<template>
  <the-header></the-header>
 <stored-resources :resources="storedResources"></stored-resources>
</template>
<script>
import StoredResources from "@/components/LearningResources/StoredResources.vue";
import theHeader from "@/components/UI/TheHeader.vue";
export default{
  components:{
    StoredResources,
    theHeader
  },
  data(){
    return{
      storedResources:[
        {
          id:'official-guide' , title:'Official Guide' , description:'The official Vue JS Documentation', link:'https://vuejs.org/guide/introduction'
        },
        {
          id:'Google' , title:'Google' , description:'Learn to google..' , link:'https://google.com'
        },
      ]
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>

