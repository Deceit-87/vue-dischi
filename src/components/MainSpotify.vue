<template>
  <div class="album-container">
    <ul class="album-list">

         <Album 
         v-for="(album,index) in setFilter()"
          :key="index"
          :patate="album"/>

    </ul>

    <div class="select-album">

      <select 
      v-model="sctAlbums" 
      name="genre">
        <option 
        v-for="(album,genre) in albums"
        :key="genre"
        :value="album.genre">{{album.genre}}
        </option>
       
      </select>

    </div>
 
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
          sctAlbums: '',

      }
   },
   methods: {
       fetchAlbums:function(){
           axios.get('https://flynn.boolean.careers/exercises/api/array/music')
           .then( res =>{
               this.albums = res.data.response;

           })
           .catch(err =>{
               console.error(err.response);
               this.albums = [];
           })
         
          
        },
        setFilter:function(){
               let albumFiltred = [];
               for (let i = 0; i < this.albums.length; i++) {
                    if (( this.sctAlbums != "") && ( this.sctAlbums != "All")) {
                        if ( this.albums[i].genre == this.sctAlbums ) {
                          albumFiltred.push( this.albums[i] );
                        }
                        else {
                          this.album = albumFiltred;
                          }
                        } 
                    else {
                       albumFiltred.push( this.albums[i] );
                    }
               }
               return albumFiltred;
         },
              genreArray:function(){
                console.log(this.albums.genre)
              },
           
        //  genreArray:function(){
        //    let selectOpt = [];
        //     let genre = this.albums.genre;
           

        //    for (let i = 0; i < this.albums.length; i++) {
        //      if(selectOpt.includes(genre[i]) === false){
        //        selectOpt.push(genre[i]);
        //       console.log( selectOpt)
        //      }
        //      else{
        //        return selectOpt;

        //      }
        //                    console.log( selectOpt)

        //    }
           
        //  },

    },

  created(){
        this.fetchAlbums();
  
  },
}
</script>

<style lang="scss" scoped>

.select-album{
    position: absolute;
    top: 2%;
    left: 50%;
    transform: translatex(-50%);
}

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