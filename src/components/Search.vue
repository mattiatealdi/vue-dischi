<template>
  <div>
      <select name="Genere" id="genere" v-model= "selected">
          <option disabled value="">Please select one option</option>
          <option  @click="startSearch" v-for="(genre,index) in getGenres()" :key="index" :value="genre">{{ genre }}</option>
      </select>
  </div>
</template>

<script>


export default {
name: 'Search',

props:{
    cards: Array,
},

data(){
  return{
    selected: '',    
  }
},

 created(){
        
},

methods:{
  // metodo richiamato da click e key up che generano un evento custom
  startSearch(){
    this.$emit("searchGenre", this.selected) // ^ io scateno l'evento search char e gli passo come param la stringa da cercare
  },
  
  getGenres(){
      let filteredGenres = []
      this.cards.forEach((card)=>{
            if(!filteredGenres.includes(card.genre)){
                filteredGenres.push(card.genre);
            }
        })
        return filteredGenres
  }

},



}
</script>

<style lang="scss" scoped>

@import '~bootstrap/scss/bootstrap';

span{
    color: white;
}

</style>