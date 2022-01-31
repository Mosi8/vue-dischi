<template>
  <header>
      <Logo />
  </header>
</template>

<script>
import Logo from '../commons/Logo.vue'

export default {
    name: 'Header',
    components: { 
        Logo, 
  },

}
</script>

<style lang="scss" scoped>
@import '../../assets/style/variables.scss';

header{
    height: 60px;
    padding: 10px 20px;
    background-color: $secondaryColor;
} 

</style>