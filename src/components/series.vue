<template>
     <singleSerie v-for="serieObj in serieList" :serieElement = 'serieObj' />
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
    
</style>