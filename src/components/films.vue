<template>
   <div class="films">
    <singleFilm v-for="filmObj in filmList" :filmElement = 'filmObj' />
   </div>
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
div.films{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  background-color: grey;
  padding-top: 1rem;
}


</style>