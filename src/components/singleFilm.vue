<template>
        <div class="film">
            
            <div class="titolo">
                {{ filmElement.title }}

            </div>
            
            <div class="titolo originale">
                {{ filmElement.original_title }}

            </div>
             
            <div class="lingua">
                <img v-if="isLanguageAvailable(filmElement.original_language)" :src="getImagePath(filmElement.original_language)" alt="language">
                <span v-else>
                    {{ filmElement.original_language }}
                </span>
            </div>
            
            <div class="voto">
                {{ filmElement.vote_average }}
                
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
img{
    width: 1rem;
}
    
</style>