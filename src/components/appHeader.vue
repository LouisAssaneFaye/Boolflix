<template>
    <header>
        <h1>
            BOOLFLIX
        </h1>
        <div class="searchBar">
             <input type="text" placeholder="search a movie" v-model="searchedFilm">
             <button @click="$emit('search', searchedFilm)">
                <i class="fa-solid fa-magnifying-glass"></i>
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
    display: flex;
    justify-content: space-between;
    background-color: black;
    padding-left: 1rem;
    padding-right: 1rem;
    h1{
        color: red;
    }
    div.searchBar{
    display: flex;
    align-items: center;
    input{
       margin-right: 5px;
    }
    button{
       width: 2.5em;
       height: 1.4rem;
    }
    }
}
    
</style>