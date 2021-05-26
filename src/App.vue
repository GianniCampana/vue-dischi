<template>
  <div id="app">
    <Header :arrGen="arrGen"
            @searchGenere='searchGenere' />
    <div class="main">
       <div class="cont-songs">
           <Song
            v-for="(song,index) in filterDisc" 
            :key="index"
            :song="song"
           />
       </div>
    </div>
  </div>
</template>

<script>

import axios from "axios";
import Header from "./components/Header";
import Song from "./components/Song";

export default {
  name: 'App',
  components: {
    Header,
    Song


  },
  computed:{

    filterDisc(){
      if(this.genereToSearch === ""){
        return this.songs
      }else{
        return this.songs.filter(element => element.genre === this.genereToSearch)
      }
    }
  },
  data(){
    return{
      axios,
      songs:[],
      arrGen:[],
      genereToSearch: ''
      
    }
  },
  methods:{
    searchGenere(genereToSearch){
      this.genereToSearch=genereToSearch
      this.$emit('searchGenere',genereToSearch)
    }
    
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res=>{
      this.songs=res.data.response
      this.songs.forEach(disc => {
           if(!this.arrGen.includes(disc.genre)){
             this.arrGen.push(disc.genre)
           }  
      });
    })
    .catch(err=>{
      console.log(err);
    })
  }

}
</script>

<style lang="scss">
@import '@/assets/style/general';

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main{
  width: 100%;
  height: 100vh;
  padding-top: 50px;
  padding-bottom: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgb(31, 33, 54); 
  .cont-songs{
    width: 80%;
    height: 100%;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }
}

</style>
