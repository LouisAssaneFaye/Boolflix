<template>
    <div class="serie">
            <div class="titolo">
                {{ serieElement.name }}

            </div>
            
            <div class="titolo originale">
                {{ serieElement.original_name }}

            </div>
             
            <div class="lingua">0
                <img v-if="isLanguageAvailable(serieElement.original_language)" :src="getImagePath(serieElement.original_language)" alt="language">
                <span v-else>
                    {{ serieElement.original_language }}
                </span>
            </div>
            
            <div class="voto">
                {{ serieElement.vote_average }}
                
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
    width: 1rem;
}
    
</style>