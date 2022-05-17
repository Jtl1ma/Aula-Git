<template>

<div id="main-banner">
<h1>Make Your Massa</h1>
</div>

</template>

<script>

export default {
    name: 'Banner'
}
</script>

<style scoped>
#main-banner {
   background-image: url('/imagem/banner.jpg');
    background-position: 0 -150px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start; 
}
#main-banner h1 {
    color: black;
    text-align: center;
    font-size: 60px;
    
    padding: 20px 40px;
}
</style>
