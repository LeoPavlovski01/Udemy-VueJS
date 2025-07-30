<template>
<div>
<ul>
  <li :class="{'custom-border': modelValue === 'poor'}">
    <button :class="{ active: modelValue === 'poor' }" type="button" @click="activate('poor')">Poor</button>
  </li>
  <li :class="{'custom-border': modelValue === 'average'}"><button :class="{active: modelValue === 'average'}" type="button" @click="activate('average')">Average</button></li>
  <li :class="{'custom-border': modelValue === 'great'}"><button :class="{active: modelValue === 'great'}" type="button" @click="activate('great')">Great</button></li>
</ul>
</div>
</template>
<script>
export default {
  props:['modelValue'],
  emits:['update:modelValue'],
  data(){
    return{

    }
  },
  methods:{
    activate(option){
      this.$emit('update:modelValue', option);
    }
  },
  name: "RatingControl.vue"
}
</script>

<style>
.custom-border{
  border:1px solid purple;
}
button.active {
  color: purple;
  font-weight: bold;
}
ul{
  list-style:none;
  margin:0.5rem 0;
  padding:0;
  display:flex;
}
li{
  margin:0 1rem;
  border:1px solid #ccc;
  padding:1rem;
  display:flex;
  justify-content: center;
}
button{
  font:inherit;
  border:none;
  background-color:transparent;
  cursor:pointer;
}
</style>

