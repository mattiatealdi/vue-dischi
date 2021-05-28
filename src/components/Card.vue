<template>
  <div class="col-xs-6 col-md-4 col-lg-2">
      <div class="card-container">
        <img :src="card.poster" :alt="card.title">
        <h3>{{ card.title }}</h3>
        <h4>{{ card.author }}</h4>
      </div>
      
  </div>
</template>

<script>

export default {
    name: 'Card',

    props:{
        card: Object,
    }
}
</script>

<style lang="scss">

@import '~bootstrap/scss/bootstrap';


img{
    width: 200px;
    height: 100%;
    
}
.card-container{
    margin: 50px 0;
    color:white;
    border: none;
    background-color: #2D3A46;
    min-height: 370px;
    padding: 20px;
}

h4{
    color: gray;
    font-size: 20px;
}

h3{
    font-size: 25px;
}
h3,h4{
    text-align: center;
}
</style>