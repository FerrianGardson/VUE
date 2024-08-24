<template>
  <h1>{{ info }}</h1>
  <p>{{ someInfo }}</p>
</template>

<style scoped>
h1 {
  color: red
}
</style>

<script>
export default {
  dada() {
    return {
      info: 'Title!',
      someInfo: 'Anons of message'
    }
  }
}
</script>