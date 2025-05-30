<template>
  <div>
    <h2>Manage Goals</h2>
    <input v-model="goal" type="text">
    <button @click="saveGoal">Add goal</button>
    <p>{{newGoal}}</p>
    <alert v-if="error" :text="error" :color="'red'"></alert>
  </div>
</template>

<script>
import Alert from "@/components/Alert.vue";
export default {
  name: "ManageGoals.vue",
  components:{
    Alert
  },
  data(){
    return{
      goal:'',
      error:null,
      newGoal:null,
      // goal ( with v-model )
    }
  },
  watch:{
    // goal(val){
    //   console.log('Val : ' , val);
    // }
  },
  methods:{
    saveGoal(){
     if(this.goal === ''){
      this.error = 'Input cant be empty';
      this.newGoal = null;
     }
     else{
       this.error = null;
       this.newGoal = this.goal;
     }
     // this.error = null;
    }
  },
}
</script>

<style scoped>
</style>