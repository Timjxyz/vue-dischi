<template>
    <div>
        <img :src="img" :alt="text">
    </div>
</template>

<script>
export default {
    name:"MyLogo",
    props:{
        'img':String,
        'text':String
    }
}
</script>

<style scoped>
    img{
        height: 50px;
        border-radius: 25px;
    }
</style>