<script>
export default {
  name: "Alert.vue",
  props:['text','color']
}
</script>

<template>
  <div :style="{backgroundColor: color === 'red' ? 'crimson' : 'green'}">
    <p style="color:white;">This is the Alert</p>
    <h2 style="color:white;">{{text}}</h2>
  </div>
</template>

<style scoped>
div {
  margin: 2rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
}
section header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>