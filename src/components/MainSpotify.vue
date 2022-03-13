<template>
  <div class="album-list">
    <ul>

         <Album 
         v-for="(album,index) in albums"
          :key="index"
          :album="album"/>

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

.album-list{
    width: 1155px;
    margin: 0 auto;
    height: 750px;
    border: 2px solid black;
    margin-top: 80px;
}
</style>