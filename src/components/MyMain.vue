<template>
    <main>
        <div class="caricamento" v-if=" loadingInProgress==true">
            <img src="https://static.movietele.it/files/styles/image-w300/public/images/2022/01/mtv.png" alt="">
            <h1>Caricamento...</h1>
        </div>
        <div v-else class="container">
            <div class="row">
                
                    <OneAlbum 
                        v-for="(discItem, index) in filteredDisc" 
                        :key="index" 
                        :album="discItem" 
                    />
                
            </div>
        </div>
        
    </main>
</template>

<script>
const axios = require('axios');
import OneAlbum from "./partials/OneAlbum.vue"
export default {
    name:"MyMain",
    components:{
        OneAlbum
    },
    props:{
        'selectedGenre':String
    },
    data() {
        return {
            discs: [],
            genres:[],
            endpoint: 'https://flynn.boolean.careers/exercises/api/array/music',
            loadingInProgress: true,
        }
    },
    computed:{
        filteredDisc(){
            if(this.selectedGenre==""){
                return this.discs;
            }else{

            return this.discs.filter(disc=>{
                return disc.genre==this.selectedGenre;
            });
            }
        }
    },
    
    created() {
        this.loadingInProgress=true
           
        // Make a request for a user with a given ID
        axios
        .get(this.endpoint)
        
        .then((response) => {
            this.discs = response.data.response;
            this.loadingInProgress = false;

            this.discs.forEach(disc=>{
                if(!this.genres.includes(disc.genre)){
                    this.genres.push(disc.genre);
                }
                
            })
            this.$emit('genresReady', this.genres)
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
        
    
    },
    

}
</script>

<style scoped lang="scss">
    main{
        min-height: calc(100vh - 80px);
        padding-top: 50px;
        background-color: #1e2d3b;
        position: relative;
    }
    .caricamento{
        display: flex;
        align-items: center;
        flex-direction: column;
        height: calc(100vh - 80px);
        h1{
            color: #fff;
        
        }
        
    }
</style>