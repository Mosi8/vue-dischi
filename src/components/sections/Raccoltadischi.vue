<template>
    <section class="container">
        <div v-if="!loading" class="row justify-content-between">
            <Disco v-for="(elemento, index) in dischiArray" :key="index" class="col-2 mx-1 mb-3 p-3" :dettagli="elemento"/>
        </div>
        <Loader v-else />
    </section>
</template>

<script>
import axios from "axios";
import Disco from '../commons/Disco.vue'
import Loader from '../commons/Loader.vue'


export default {
    name: 'Raccoltadischi',
    components: {
        Disco,
        Loader,
    },
    data(){
        return {
            api: "https://flynn.boolean.careers/exercises/api/array/music",
            dischiArray: [],
            loading: true,
        }
    },
    created(){
        this.getDischi();
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
        }
    },
}

</script>


<style lang="scss" scoped>

.container {
    padding: 50px 250px;
}

</style>