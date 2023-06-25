<template>
    <header>
        <div class="searchBar">
        <input type="text" placeholder="search a movie" v-model="searchedFilm">
        <button @click="$emit('search', searchedFilm)">

        </button>
    </div> 
        
    </header>
</template>

<script>
export default {
   
  name:'appHeader',
  data(){
    return{
        searchedFilm:'',

    }

   }

}

</script>
<style lang="scss" scoped>
header{
    div.searchBar{
    display: flex;
    align-items: center;
    input{
       margin-right: 10px;
    }
    button{
       width: 2.5em;
       height: 1.4rem;
    }
    }
}
    
</style>