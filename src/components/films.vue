<template>
    <singleFilm v-for="filmObj in filmList" :filmElement = 'filmObj' />
</template>
<script>
import singleFilm from './singleFilm.vue';
export default{
  name:'films',
  data(){
    return{
      
    }

  },
  components:{
    singleFilm,
  },
  props:{
    filmList: Array,
  },
  methods:{
  }
}
</script>
<style lang="scss" scoped>

</style>