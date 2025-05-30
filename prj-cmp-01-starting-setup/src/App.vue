<template>
<!--  <listing-resources>-->
<!--    <template #resource>-->
<!--     <list-items :resources="storedResources"></list-items>-->
<!--    </template>-->
<!--  </listing-resources>-->
  <ul>
    <learning-resource :resource="res" v-for="res in storedResources" :key="res.id"></learning-resource>
  </ul>

</template>
<script>
import LearningResource from "@/components/LearningResources/LearningResource.vue";
export default{
  components:{
    LearningResource
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