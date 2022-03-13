<template>
  <div class="album-container">
    <ul class="album-list">

         <Album 
         v-for="(album,index) in albums"
          :key="index"
          :patate="album"/>

    </ul>

  </div>
</template>

<script>
import axios from 'axios'

import Album from './AlbumCard.vue'

export default {
    components:{
        Album,
    },    
  data(){
      return{
          albums:[],
  
      }
   },
   methods: {
       fetchAlbums:function(){
           axios.get('https://flynn.boolean.careers/exercises/api/array/music')
           .then( res =>{
               this.albums = res.data.response;
               console.log(this.albums);

           })
        //    .catch(err =>{
        //        console.error(err.response);
        //        this.albums = [];
        //    })
         
          
        }
  },
  created(){
        this.fetchAlbums();
  
  },
}
</script>

<style>

.album-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 1195px;
    margin: 0 auto;
    height: 750px;
    margin-top: 80px;
    
}
.album-list{
        display: contents;

}
</style>