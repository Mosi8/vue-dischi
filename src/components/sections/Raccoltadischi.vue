<template>
    <section class="container">
        <span>Filtra per generi: <Filtri  @gen="getGenere"/></span>
        <span>Filtra per artista: <Artisti  @artis="getArtista"/></span>
        <div v-if="!loading" class="row justify-content-center">
            <Disco v-for="(elemento, index) in mostraGenere" :key="index" class="col-2 mx-2 mb-3 p-3" :dettagli="elemento"/>
        </div>
        <Loader v-else />
    </section>
</template>

<script>
import axios from "axios";
import Disco from '../commons/Disco.vue'
import Loader from '../commons/Loader.vue'
import Filtri from '../commons/Filtri.vue'
import Artisti from '../commons/Artisti.vue'


export default {
    name: 'Raccoltadischi',
    components: {
        Disco,
        Loader,
        Filtri,
        Artisti,
    },
    data(){
        return {
            api: "https://flynn.boolean.careers/exercises/api/array/music",
            dischiArray: [],
            loading: true,
            genere: "",
            artista: "",
        }
    },
    created(){
        this.getDischi();
    },
    computed: {
        mostraGenere(){
            return this.dischiArray.filter( (elemento) => {
                return (elemento.genre.includes(this.genere))&&
                (elemento.author.includes(this.artista));
            });
        }
    },
    methods: {
        getDischi(){
            axios
                .get(this.api)
                .then( (risposta) => {
                    this.dischiArray = risposta.data.response;
                    console.log(this.dischiArray);
                    this.loading = false;
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
        getGenere(genereSelezionato){
            this.genere = genereSelezionato;
            console.log(this.genere);
        },
        getArtista(artistaSelezionato){
            this.artista = artistaSelezionato;
            console.log(this.artista);
        }
    },
}

</script>


<style lang="scss" scoped>

.container {
    padding: 50px 200px;
    text-align: center;

    span {
        color: #fff;
        font-size: 20px;
        margin: 0 20px 20px 0;
        display: inline-block;
    }
}

</style>