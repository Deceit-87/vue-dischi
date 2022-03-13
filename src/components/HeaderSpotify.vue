<template>
  <section>
     <div class="header">
          <i class="fa-brands fa-spotify logo"></i>
     </div>
  </section>
</template>

<script>
export default {
    name:'HeaderSpotify',
}
</script>

<style>
.header{
    background: rgba(255, 255, 255, 0.1);
    height: 70px;
    display: flex;
    align-items: center;
   
}
 .logo{  
    padding: 5px 0 5px 5px;
    font-size: 48px;
    color: #1ed760;
    padding-left: 15px;
    }
</style>