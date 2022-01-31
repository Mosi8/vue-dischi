<template>
  <main>
      <Raccoltadischi />
  </main>
</template>

<script>
import Raccoltadischi from '../sections/Raccoltadischi.vue'

export default {
  name: 'Main',
  components: {
    Raccoltadischi,
  },
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/variables.scss';

  main {
    background-color: $maincolor;
    min-height: 100vh;
  }
</style>