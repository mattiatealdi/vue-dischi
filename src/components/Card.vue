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
    background-color: #2D3A46
}
.card-container{
    color:white;
    border: none;
}

h4{
    color: gray
}

h3,h4{
    text-align: center;
    min-height: 40px;
}
</style>