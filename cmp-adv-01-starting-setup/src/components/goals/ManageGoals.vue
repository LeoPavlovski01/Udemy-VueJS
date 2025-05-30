<template>
  <div>
    <h2>Manage Goals</h2>
    <input v-model="goal" type="text">
    <button @click="saveGoal">Add goal</button>
    <p>{{newGoal}}</p>

    <teleport to="body">
      <alert v-if="invalidInput">
        <template #text>
          <div style="display:flex; align-items:center; justify-content: space-between">
            <h2>Error!!</h2>
            <button @click="closeDialog">X</button>
          </div>
        </template>
        <template #reason>
          <h2>{{errorText}}</h2>
        </template>
      </alert>
    </teleport>
  </div>
</template>

<script>
import Alert from "@/components/layout/Alert.vue";
export default {
  name: "ManageGoals.vue",
  components:{
    Alert
  },
  data(){
    return{
      goal:'',
      invalidInput:false,
      error:null,
      newGoal:null,
      errorText:'',
      // goal ( with v-model )
    }
  },
  watch:{
    // goal(val){
    //   console.log('Val : ' , val);
    // }
  },
  methods:{
    closeDialog(){
      this.invalidInput = false;
    },
    saveGoal(){
     if(this.goal === ''){
      this.invalidInput = true;
      this.errorText= 'Invalid Input, Try Adding an Input!'
     }
     else{
       this.invalidInput = false;
       this.errorText = ''
     }
     // this.error = null;
    }
  },
}
</script>

<style scoped>
</style>