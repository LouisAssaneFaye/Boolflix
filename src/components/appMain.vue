<template>
     <main>
        <searchBar @search="getSearchedFilm, getSearchedSerie" />
        <div v-for="filmObj in filmList">
            
            <div class="titolo">
                {{ filmObj.title }}

            </div>
            
            <div class="titolo originale">
                {{ filmObj.original_title }}

            </div>
             
            <div class="lingua">
                {{ filmObj.original_language }}
            </div>
            
            <div class="voto">
                {{ filmObj.vote_average }}
                
            </div>

        </div>

        <div v-for="serieObj in serieList">
            
            <div class="titolo">
                {{ serieObj.name }}

            </div>
            
            <div class="titolo originale">
                {{ serieObj.original_name }}

            </div>
             
            <div class="lingua">
                {{ serieObj.original_language }}
            </div>
            
            <div class="voto">
                {{ serieObj.vote_average }}
                
            </div>

        </div>

     </main>
</template>
<script>
import searchBar from './searchBar.vue';
import axios from 'axios';
export default{
  name:'appMain',
  data(){
    return{
        filmList:[],
        serieList:[],
        apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=dcfd41668f40665b3e285e3308a1c9d3&query=',
        APIKey: 'dcfd41668f40665b3e285e3308a1c9d3',
        apiUrlTwo: 'https://api.themoviedb.org/3/search/tv?api_key=dcfd41668f40665b3e285e3308a1c9d3&language=it_IT&query=',
    }

  },
  components:{
    searchBar,
  },
  methods:{
        getSearchedFilm(needle=''){
            axios.get(`${this.apiUrl}${needle}`)
           .then((response)=> {
           console.log(response.data.results);
           this.filmList=response.data.results;
        
           })
          .catch(function (error) {
          console.log(error);
          });

        },
        getSearchedSerie(needle=''){
            axios.get(`${this.apiUrlTwo}${needle}`)
           .then((response)=> {
           console.log(response);
           this.serieList=response.data.results;
        
           })
          .catch(function (error) {
          console.log(error);
          });

        }
  },
  created(){
        this.getSearchedFilm(),
        this.getSearchedSerie()
  }
}
</script>
<style lang="scss" scoped>
    
</style>