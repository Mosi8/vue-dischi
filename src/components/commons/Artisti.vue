<template>
        <select name="artista" id="artista"
        v-model="artistaSelezionato"
        @change="$emit('artis', artistaSelezionato)"
        >
            <option value="">All</option>
            <option v-for="(elemento, index) in artistiArray" 
            :key="index"
            :value="elemento">{{elemento}}</option>
        </select>
</template>

<script>
import axios from "axios";
export default {
    name: 'Artisti',
    data(){
        return {
            api: "https://flynn.boolean.careers/exercises/api/array/music",
            artistiArray: [],
            artistaSelezionato: "",
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
                    this.loading = false;
                    this.dischiArray.forEach(element => {
                        if (!this.artistiArray.includes(element.author))
                        this.artistiArray.push(element.author);
                    });
                    console.log(this.artistiArray);
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
    }

}
</script>

<style>

</style>