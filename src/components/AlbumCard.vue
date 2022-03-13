<template>
  <li class="card-wrapper">
      <figure class="card-thumb">

          <img :src="patate.poster" alt="">

      </figure>
      <div class="card-info">

          <h3>
              {{patate.title}}
          </h3>
          <p>
              {{patate.author}}
          </p>
          <p>
              {{patate.year}}
          </p>

      </div>
  </li>
</template>

<script>
export default {
    props:{
       patate:{
        type: Object,
        required: true,
        }
    }
}
</script>

<style lang="scss" scoped>
.card-wrapper{
    padding: 20px;
    display: flex;
    align-items: center;
    flex-direction: column;
    max-height: 357px;
    max-width: 16%;
    margin: 0 20px 20px;
    background: rgba(255, 253, 253, 0.1);
    .card-thumb{
        img{
            aspect-ratio: 1;
            object-fit: cover;
            object-position: center;
            width: 100%;
        }
    }
    .card-info{
        font-size: 16px;
        width: 95%;
        color: rgba(255, 255, 255, 0.356);
        h3{
             color: white;
            font-size: 20px;
            text-transform: uppercase;
            padding: 20px 0;
        }
       
    }
 
}
   

</style>>

