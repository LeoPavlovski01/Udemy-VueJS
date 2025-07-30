<template>
  <div class="icons">
    <i class="mdi mdi-instagram icon" :class="{active:modelValue === 'instagram'}" @click="handleSocialMedia('instagram')"></i>
    <i class="mdi mdi-facebook icon" :class="{active:modelValue === 'facebook'}" @click="handleSocialMedia('facebook')"></i>
    <i class="mdi mdi-twitter icon" :class="{active:modelValue === 'twitter'}" @click="handleSocialMedia('twitter')"></i>
  </div>
</template>

<script>
export default {
  props:['modelValue'],
  emits:['update:modelValue'],
  name: "SocialMedia.vue",
  data(){
    return{

    }
  },
  methods:{
    handleSocialMedia(option){
      this.$emit('update:modelValue' , option);
    }
  },
}
</script>

<style scoped>
.active{
  color:red;
}
.icons{
  display:flex;
  align-items:center;
  justify-content: space-between;
}
.icon{
  display:flex;
  align-items:center;
  justify-content: center;
  font-size:80px;
}
</style>