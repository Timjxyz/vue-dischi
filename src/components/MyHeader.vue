<template>
<header>
    <MyLogo  v-for="(logo, index) in logos" 
            :key="index"
            :img="logo.src" 
            :text="logo.titolo" />
</header>
  
</template>

<script>

import MyLogo from "./partials/MyLogo.vue"
export default {
    name:"MyHeader",

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

            ]
        }
    }
}
</script>

<style lang="scss" scoped>
header{
    height: 80px;
    padding: 10px;
    display: flex;
    align-items: center;
    background-color: #2e3a46;
    
}

</style>