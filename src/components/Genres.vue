<template>
<section>
    <select 
             v-model='genereToSearch' class="generi"
             @change="$emit('searchGenere', genereToSearch)">
        <option value="">
            GENERI
        </option>
        <option
        v-for="(genere, index) in arrGen" 
        :key="index" 
        :value="genere"
        >{{ genere }}</option>
        
    </select>
</section>
</template>

<script>

import axios from "axios";

export default {
    name: 'Generi',
    components: {
    },
    props:{
      arrGen: Array
    },
    methods:{
       
    },

     data(){
    return{
      axios,
      songs:[],
      genereToSearch: ''
      
    }
  },

  created(){

  }
}

</script>


<style lang='scss' scoped>
section{

    width: 100%;
    height: 70px;
    display: flex;
    align-items: center;
    justify-content: center;
        .generi{
        width: 200px;
        height: 60px;
        margin-left: 30px;
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: rgb(0, 0, 95);
        border-radius: 1000px;
        cursor: pointer;
         &:hover{
            transform: scale(1.02, 1.02);
            box-shadow: 0 5px 5px rgba($color: black, $alpha: 0.3);
         }
        }
        .lista-generi{
        height: 50px;
        background-color: rgb(0, 0, 105);
        border-radius: 1000px;
        border: black solid 1px;
        margin-left: 20px;
        padding-left: 20px;
        padding-right: 20px;
        ul{
            height: 50px;
            list-style: none;
            display: flex;
            align-items: center;
            justify-content: space-around;
            padding-left: 0;
            li{
                color: white;
                text-transform: uppercase;
                cursor: pointer;
                h1{
                    font-size: 25px;
                }
            }
        }
        }
}

</style>

 
