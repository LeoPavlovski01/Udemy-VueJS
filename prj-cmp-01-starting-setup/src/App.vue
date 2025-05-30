<template>
<ul v-for="item in storedResources" :key="item.id">
<li>
  {{item}}
</li>
</ul>
</template>

<script>
export default{
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