<template>
    <main>
        <appHeader @search="getMoviesAndSeries" />
         <div class="films">
            <films :filmList="filmList" />
         </div>
         <div class="series">
           <series :serieList="serieList" />
         </div>
    </main>
</template>

<script>
import appHeader from './appHeader.vue';
import films from './films.vue';
import series from './series.vue';
import axios from 'axios';
export default{
  name:'appMain',
  data(){
    return{
        filmList:[],
        serieList: [],
        apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=dcfd41668f40665b3e285e3308a1c9d3&query=',
        apiUrlTwo: 'https://api.themoviedb.org/3/search/tv?api_key=dcfd41668f40665b3e285e3308a1c9d3&language=it_IT&query=',
        APIKey: 'dcfd41668f40665b3e285e3308a1c9d3',
    }

  },
  components:{
    appHeader,
    films,
    series,
},
  methods:{
        getMoviesAndSeries(arg){
            this.getSearchedFilm(arg),
            this.getSearchedSerie(arg)
        },
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
           console.log(response.data.results);
           this.serieList=response.data.results;
        
           })
          .catch(function (error) {
          console.log(error);
          });

        }
        
  },
  created(){
        this.getSearchedFilm(),
        this.getSearchedSerie(),
        this.getMoviesAndSeries()
  }
  
}
</script>

<style lang="scss" scoped>
main{
    background-color: gray;
    height: 100vh;
}
    
</style>