<template>
  <main>
      <search 
        @searchGenre= "searching"
      />
      <div class="row mt-20">
        <Card
          v-for="card in filteredMusic"
          :key = "card.id"
          :card ="card"
        />
      </div>
  </main>
</template>



<script>

import axios from 'axios';
import Card from './Card.vue';
import Search from './Search.vue';



export default {
  components: { 
    Card,
    Search,
  },
    name: 'MainComp',


    data(){
        return{
            axios,
            result: {},
            cards: [],
            loading: true,
            genres: [],
            genreToSearch: '',
        }
    },
    computed: {
        filteredMusic(){
            let cleanArr = this.cards;
            if(this.genreToSearch == ''){
                return cleanArr;
            }
            return cleanArr.filter(item => item.genre.toLowerCase().includes(this.genreToSearch.toLowerCase()));
        }
    },
    created(){
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

    /* methods:{
        genreFiltered(){
            this.cards.forEach(genre){
                if(cards.genre.includes(gener))
            }
        }
    }, */
    methods:{
        searching(text){
            this.genreToSearch = text;
        }
    }
    
}



</script>

<style style="scss" scoped>
main{
    background-color: black;
    
}
.row{
        min-width: 1170px;
        display: flex;
        justify-content: center;
        
    }

select{
    padding: 20px 40px;
    margin: 40px 0;
}
</style>