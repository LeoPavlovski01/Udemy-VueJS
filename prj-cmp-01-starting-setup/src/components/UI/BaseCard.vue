<script>
export default {
  name: "BaseCard.vue"
}
</script>

<template>
<div>
<slot name="header">
</slot>
  <slot name="description">
  </slot>
  <slot name="link">
    <nav>

    </nav>
  </slot>
</div>
</template>

<style scoped>

</style>