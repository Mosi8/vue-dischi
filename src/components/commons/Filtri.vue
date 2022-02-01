<template>
        <select name="genere" id="genere"
        v-model="genereSelezionato"
        @change="$emit('gen', genereSelezionato)"
        >
            <option value="">All</option>
            <option v-for="(elemento, index) in generiArray" 
            :key="index"
            :value="elemento">{{elemento}}</option>
        </select>
</template>

<script>
import axios from "axios";
export default {
    name: 'Filtri',
    data(){
        return {
            api: "https://flynn.boolean.careers/exercises/api/array/music",
            generiArray: [],
            genereSelezionato: "",
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
                        if (!this.generiArray.includes(element.genre))
                        this.generiArray.push(element.genre);
                    });
                    console.log(this.generiArray);
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