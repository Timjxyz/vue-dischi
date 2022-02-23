<template>
   <div class="ms-col">
        <img :src="album.poster" :alt="album.author">
        <h2>{{album.title}}</h2>
        <div class="text">{{album.author}}</div>
        <div class="text">{{album.gender}}</div>
        <div class="text">{{album.year}}</div>
    </div>
</template>

<script>
export default {
    name:"OneAlbum",
    props:{
        'album':Object
    }
}
</script>

<style scoped lang="scss">
    .ms-col{
        width:calc(100% / 5 - 20px);
        margin: 10px;
        padding: 20px;
        text-align: center;
        background-color: #2e3a46;
        img{
            width: 200px;
            height: 200px;
            object-fit: cover;
        }
        h2{
            color: #fff;
        }
        .text{
            color: gray;
        }
    }
</style>