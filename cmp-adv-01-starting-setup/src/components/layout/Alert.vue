<script>
export default {
  name: "Alert.vue",
}
</script>

<template>
  <dialog open>
    <slot name="text"></slot>
    <div>
      <slot name="reason"></slot>
    </div>
  </dialog>
</template>

<style scoped>
dialog{
  margin:0;
  position:fixed;
  top:20vh;
  left:30%;
  width:40%;
  background-color:white;
  box-shadow:0 2px 8px rgba(0,0,0,0.26);
  padding:1rem;
}
</style>