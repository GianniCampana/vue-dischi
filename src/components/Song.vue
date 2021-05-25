<template>

      
        <div class="song">
          <img :src="song.poster" alt="img song">
          <h1>{{song.title}}</h1>
          <h3>{{song.author}}</h3>
          <h4>{{song.year}}</h4>
        </div>
      
  
</template>

<script>
export default {
    name:'Song',
    props:{
      song: Object
      
    }
}
</script>

<style lang="scss" scoped>



    .song{
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 150px;
      height: 275px;
      background-color: rgba(156, 156, 156, 0.3);
      margin: 3%;
      padding: 2%;
      cursor: pointer;
       &:hover{
       transform: scale(1.05, 1.05);
       filter: brightness(130%);
       box-shadow: 0 15px 15px rgba($color: black, $alpha: 0.5);
  }

      img{
      width: 130px;
      margin-bottom: 10px;

      }
      h1{
        width: 150px;
        font-size: 16px;
        text-transform: uppercase;
        text-align: center;
        font-weight: 600;
        color: white;
      }
      h3{
        font-size: 15px;
        color: white;
        text-align: center;
      }
      h4{
        font-size: 15px;
        color: white;
        text-align: center;
      }
      }




</style>