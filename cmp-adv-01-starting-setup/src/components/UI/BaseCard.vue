<template>
  <div>
    <section>
      <header>
        <slot name="header">
          <p>The Default</p>
        </slot>
      </header>
    </section>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "BaseCard.vue",
  mounted(){
    console.log('SLOTS:  ', this.$slots);
  },
}
</script>

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