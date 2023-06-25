<template>
        <div class="film">
            <div class="informations">
                
                <div class="titolo">
                    <span>
                        Titolo: 
                    </span>
                    {{ filmElement.title }}
                </div>
            
                <div class="titolo originale">
                    <span>
                        Titolo originale: 
                    </span>
                    {{ filmElement.original_title }}
                </div>
             
                <div class="lingua">
                    <img v-if="isLanguageAvailable(filmElement.original_language)" :src="getImagePath(filmElement.original_language)" alt="language">
                    <span v-else>
                        Lingua: {{ filmElement.original_language }}
                    </span>
                </div>
            
                <div class="voto">
                    <span>Voto:</span>
                    <div v-for="n in Math.round(filmElement.vote_average / 2)">
                        <i class="fa-solid fa-star"></i>
                    </div>

                    <div v-for="n in (5 - Math.round(filmElement.vote_average / 2))">
                        <i class="fa-regular fa-star"></i>
                    </div>
                </div>

                <div class="overview">
                   <span>
                     Overview:
                   </span> 
                   {{ filmElement.overview }}
                </div>

            </div>

            <div class="cover">
                <img :src="`https://image.tmdb.org/t/p/w342/${filmElement.backdrop_path}`" alt="cover del film non disponibile" >
            </div>

        </div>    
    
</template>

<script>
export default {
    name: 'singleFilm',
    props:{
        filmElement: Object,
    },
    data(){
        return{
            availableFlags:[
                'en.png',
                'es.png',
                'fr.png',
                'it.png',
            ]
        }
    },
    methods:{
    isLanguageAvailable(language){
        if(this.availableFlags.includes(language+'.png')){
            return true
        }else{
            return false;
        }
    },
    getImagePath(imgSource){
        return new URL (`../assets/img/flags/${imgSource}.png`, import.meta.url).href;
    }
  }
    
}
</script>

<style lang="scss" scoped>

div.film{
    width: 20rem;
    position: relative;
    div.cover{
        display: none;
        margin-bottom: 1rem;
        background-color: black;
        color: white;
        height: 25rem;
        width: 20rem;
        text-align: center;
      img{
        height: 25rem;
        width: 20rem;
      }
    }
    div.informations:hover~div.cover{
        display: inline;
        position: absolute;
        top: 0;
        z-index: 1;
    }
    div.informations{
        color: white;
        background-color: black;
        width: 20rem;
        height: 25rem;
        overflow-y: auto;
        margin-bottom: 1rem;
        div.lingua{
            img{
                width: 3rem;
            }
        }
        span{
            font-weight: bold;
        }
        *{
            margin-top: 0.5rem;
        }
        div.overview{
           span{
              margin-left: 0px;
              margin-right: 10px;
            }
        }
       div.voto{
            display: flex;
            align-items: center;
            span{
                margin-right: 3rem;
            }
        }
   }

}


</style>