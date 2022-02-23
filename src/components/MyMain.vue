<template>
    <main>
        <div class="caricamento" v-if=" loadingInProgress==true">
            <img src="https://static.movietele.it/files/styles/image-w300/public/images/2022/01/mtv.png" alt="">
            <h1>Caricamento...</h1>
        </div>
        <div v-else class="container">
            <div class="row">
                
                    <OneAlbum 
                        v-for="(album, index) in listaAlbum" 
                        :key="index" 
                        :album="album" 
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
    data() {
        return {
            listaAlbum: [],
            endpoint: 'https://flynn.boolean.careers/exercises/api/array/music',
            loadingInProgress: true,
        }
    },
    methods: {
        getAlbum() {
            
            // Make a request for a user with a given ID
            axios.get(this.endpoint)
            .then((response) => {
                this.listaAlbum = response.data.response;
                this.loadingInProgress = false;
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            });
        }
    },
    created() {
        this.loadingInProgress=true
    },
    mounted() {
        this.getAlbum();
    },

}
</script>

<style scoped lang="scss">
    main{
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