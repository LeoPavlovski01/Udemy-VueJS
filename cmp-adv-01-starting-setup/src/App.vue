<template>
  <div>
<!--    <the-header></the-header>-->
    <header-component></header-component>
    <button @click="handleGoals('active-goals')">Active Goals</button>
    <button @click="handleGoals('manage-goals')">Manage Goals</button>
    <button @click="handleGoals('inactive-goals')">Inactive Goals</button>

<!--    <component :is="selectedGoal"></component>-->

<!--    <active-goals v-if="selectedGoal === 1"></active-goals>-->
<!--    <manage-goals v-if="selectedGoal === 2"></manage-goals>-->
<!--    <inactive-goals v-if="selectedGoal === 3"></inactive-goals>-->

<!--    <badge-list></badge-list>-->
<!--    <user-info :active-user="activeUser"></user-info>-->
<!--    <course-goals #default="slotProps">-->
<!--        <h2>{{slotProps.item}}</h2>-->
<!--        <p>{{slotProps.customProp}}</p>-->
<!--    </course-goals>-->
<!--    Removed from the dom when we change through components-->
    <keep-alive>
      <component :is="selectedGoal"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from "@/components/layout/TheHeader.vue";
import ActiveGoals from "@/components/goals/ActiveGoals.vue";
import ManageGoals from "@/components/goals/ManageGoals.vue";
import InactiveGoals from "@/components/goals/InactiveGoals.vue";
// import BadgeList from "@/components/BadgeList.vue";
// import UserInfo from "@/components/UserInfo.vue";
// import CourseGoals from "@/components/CourseGoals.vue";
export default {
  components:{
    InactiveGoals,
    ActiveGoals,
    ManageGoals,
    headerComponent:TheHeader,
    // badgeList:BadgeList,
    // userInfo:UserInfo,
  },
  data() {
    return {
      selectedGoal:'active-goals',
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
  methods:{
    handleGoals(cmp){
      this.selectedGoal = cmp;
      // switch(item){
      //   case false:
      //     return this.goals = false;
      //   case true:
      //     return this.goals = true;
      // }
    }
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