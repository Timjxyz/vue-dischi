<template>
<header>
    <MyLogo  v-for="(logo, index) in logos" 
            :key="index"
            :img="logo.src" 
            :text="logo.titolo" />
    <select v-model="selectedGenre" @change="$emit('selectedGenreEvt',selectedGenre)">
        <option value="">Seleziona un genere</option>
        <option v-for="(genre, index) in genresList" :value="genre" :key="index">{{genre}}</option>

    </select>

</header>
  
</template>

<script>

import MyLogo from "./partials/MyLogo.vue"
export default {
    name:"MyHeader",
    props:{
        'genresList':Array,

    },

    components:{
        MyLogo
    },
    data(){
        return{
            logos:[
                {
                   src:"https://static.movietele.it/files/styles/image-w300/public/images/2022/01/mtv.png",
                   titolo:"Logo mtv"
                }

            ],
            selectedGenre:'',
        }
    }
}
</script>

<style lang="scss" scoped>
header{
    height: 80px;
    padding: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #2e3a46;
    
}

</style>