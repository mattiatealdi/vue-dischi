<template>
  <div>
      <select name="Genere" id="genere" v-model= "selected">
          <option disabled value="">Please select one option</option>
          <option  @click="startsearch" v-for="(genre,index) in filteredGenres" :key="index" :value="genre">{{ genre }}</option>
      </select>
      <span>{{ selected }}</span>
  </div>
</template>

<script>

import axios from 'axios';

export default {
name: 'Search',


data(){
  return{
    selected: '',
    cards: [],
    filteredGenres: [],
  }
},

 created: {
    filterGenre(){
        this.cards.forEach((card)=>{
            let genre = card.genre;
            if(!this.filteredGenres.includes(genre)){
               this.filteredGenres.push(genre);
            }
        })
    }
},

methods:{
  // metodo richiamato da click e key up che generano un evento custom
  startSearch(){
    this.$emit("searchGenre", this.selected) // ^ io scateno l'evento search char e gli passo come param la stringa da cercare
  },
  // chiamato da reset pulisce il testo da ricercare e richiama la func di recerca
  resetSearch(){
    this.stringToSearch = "" // ^ qua pulisco la stringa e BASTA
    this.startSearch(); // . qua richiamo l'evento che scatena la ricerca e quindi mi passa una stringa vuota
  }

},

mounted(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then( res => {
                console.log(res.data);
                this.result = res.data;
                this.cards = this.result.response;
                console.log(this.cards);
                this.loading = false;
            })
            .catch( err => {
                console.log(err);
            })
    },

}
</script>

<style lang="scss" scoped>

@import '~bootstrap/scss/bootstrap';

</style>