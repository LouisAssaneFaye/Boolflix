<template>
    <div class="searchBar">
        <input type="text" placeholder="search a movie" v-model="searchedFilm">
        <button @click="$emit('search', searchedFilm)">

        </button>
    </div> 
</template>

<script>
export default {
    name: 'searchBar',
    data(){
        return{
            searchedFilm: '',
        }
    }
}

</script>

<style lang="scss" scoped>
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
    
</style>