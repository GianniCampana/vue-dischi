<template>

<div class="cont">
    <img src="../assets/logo-small.svg" alt="">
    <Genres @searchGenere="searchGenere"  :arrGen="arrGen" />
</div>
    
</template>

<script>


import Genres from "./Genres";

export default{
    name: 'Header',
    components: {
        Genres
    },
     props:{
        arrGen: Array
    },
    methods:{
          searchGenere(genereToSearch){
        this.genereToSearch= genereToSearch
        this.$emit('searchGenere',genereToSearch)
      }
    }
}

</script>

<style lang="scss" scoped>
.cont{
    display: flex;
    align-items: center;
    width: 100%;
    height: 70px;
    background-color: rgb(56, 58, 75);
    img{
        width: 3%;
        margin-left: 20px;
        cursor: pointer;
    }   
}

</style>


