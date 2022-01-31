<template>
  <div class="disco text-center">
      <img :src="dettagli.poster">
      <h5>{{dettagli.title}}</h5>
      <p>{{dettagli.author}}</p>
      <span>{{dettagli.year}}</span>
  </div>
</template>

<script>
export default {
    name: 'Disco',
    props: {
        dettagli: Object,
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/variables.scss';
.disco {
    background-color: $secondaryColor;
    color: #fff;
    img{
        width: 100%;
    }
    h5 {
        margin: 15px 0
    }

    p {
        margin: 0;
        color: rgb(150, 150, 150);
        font-size: $size;
    }
    span{
        color: rgb(150, 150, 150);
        font-size: $size;
    }
}

</style>