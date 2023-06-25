<template>
    <div class="serie">
            <div class="titolo">
                {{ serieElement.name }}

            </div>
            
            <div class="titolo originale">
                {{ serieElement.original_name }}

            </div>
             
            <div class="lingua">
                <img v-if="isLanguageAvailable(serieElement.original_language)" :src="getImagePath(serieElement.original_language)" alt="language">
                <span v-else>
                    {{ serieElement.original_language }}
                </span>
            </div>
            
            <div class="voto" v-for="n in Math.round(serieElement.vote_average / 2)">
                <i class="fa-solid fa-star"></i>
            </div>

            <div class="voto" v-for="n in (5 - Math.round(serieElement.vote_average / 2))">
                <i class="fa-regular fa-star"></i>
            </div>

            <div class="cover">
                <img :src="`https://image.tmdb.org/t/p/w342/${serieElement.backdrop_path}`" alt="film cover" >
            </div>

        </div>    
</template>
<script>
export default {
    
    name:'',
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
    props:{
        serieElement: Object,
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
img{
    width: 3rem;
}
    
</style>