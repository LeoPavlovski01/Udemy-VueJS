<template>
  <ul>
    <li v-for="item in goals" :key="item">
      {{item}}
    </li>
  </ul>
</template>

<script>
export default{
  data(){
    return{
      goals:['Finish the course' , 'Learn vue']
    }
  }
}
</script>