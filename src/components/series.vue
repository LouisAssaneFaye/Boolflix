<template>
     <div class="series">
        <singleSerie v-for="serieObj in serieList" :serieElement = 'serieObj' />
     </div>
</template>
<script>
import singleSerie from './singleSerie.vue';
export default{
  name:'series',
  data(){
    return{
    
    }

  },
  components:{
    singleSerie,
  },
  props:{
    serieList: Array,
  }
}
</script>
<style lang="scss" scoped>
div.series{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  padding-top: 1rem;
  background-color: grey;
}
    
</style>