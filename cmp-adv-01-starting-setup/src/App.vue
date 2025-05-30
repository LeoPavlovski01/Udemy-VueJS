<template>
  <div>
<!--    <the-header></the-header>-->
    <header-component></header-component>
    <badge-list></badge-list>
    <user-info :active-user="activeUser"></user-info>
    <course-goals #default="slotProps">
        <h2>{{slotProps.item}}</h2>
        <p>{{slotProps.customProp}}</p>
    </course-goals>
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader.vue";
import BadgeList from "@/components/BadgeList.vue";
import UserInfo from "@/components/UserInfo.vue";
import CourseGoals from "@/components/CourseGoals.vue";
export default {
  components:{
    CourseGoals,
    headerComponent:TheHeader,
    badgeList:BadgeList,
    userInfo:UserInfo,
  },
  data() {
    return {
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>