<template>
  <div id="app">
    <Header />
    <div class="main">
       <div class="cont-songs">
           <Song
           v-for="(song,index) in songs.response" 
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
  data(){
    return{
      axios,
      songs:[]
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res=>{
      this.songs=res.data
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
  height: 100%;
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
