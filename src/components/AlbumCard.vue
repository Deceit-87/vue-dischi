<template>
  <li class="card-wrapper">
      <figure class="card-thumb">

          <img :src="album.poster" alt="">

      </figure>
      <div class="card-info">

          <h3>
              {{album.title}}
          </h3>
          <p>
              {{album.author}}
          </p>
          <p>
              {{album.year}}
          </p>

      </div>
  </li>
</template>

<script>
export default {
    props:{
       album:{
        type: Object,
        required: true,
        }
    }
}
</script>

<style>

</style>