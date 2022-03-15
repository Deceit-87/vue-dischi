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
      name="genre" open>
        <option value="" disabled selected hidden>Choose Genre</option>
        <option value="All">All</option>
        <option 
        v-for="(album,genre) in genreArray()"
        :key="genre"
        :value="album">{{album}}
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
                 if (( this.sctAlbums != "") && ( this.albums[i].genre == this.sctAlbums ) ){
                   
                         albumFiltred.push( this.albums[i] );
                     }
                  else if( ( this.sctAlbums == "")||( this.sctAlbums == 'All' ) ){
                         albumFiltred = this.albums;
                  }
                }
               return albumFiltred;
         },
        // setFilter:function(){
        //        let albumFiltred = [];
        //        for (let i = 0; i < this.albums.length; i++) {
        //          if (( this.sctAlbums != "") && ( this.sctAlbums != "All")) {
        //             if ( this.albums[i].genre == this.sctAlbums ) {
        //                  albumFiltred.push( this.albums[i] );
        //              }
        //             else {
        //                 this.album = albumFiltred;
        //              }
        //           } 
        //          else {
        //                albumFiltred.push( this.albums[i] );
        //           }
        //         }
        //        return albumFiltred;
        //  },
        genreArray:function(){
          let selectOpt = [];
          
          for (let j = 0; j < this.albums.length; j++) {
              if(selectOpt.includes(this.albums[j].genre) == false){
                   selectOpt.push(this.albums[j].genre);
              }  
          }
          return selectOpt;
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
    select{
      background:#1ed760;
      border: none;
      padding: 5px 9px;
      font-size: 15px;
      font-weight: 600;
      color: #35424f;
      border-top-left-radius: 6px;
      border-top-right-radius: 6px;
    
    }
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