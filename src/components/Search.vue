<template>
  <input type="text" class="searchForm" placeholder="Search any character..." v-model="search" @keyup="searchByName">
  <i class="fas fa-search"></i>
</template>

<script>
export default {
    name: "Search",
    data(){
        return{
            search: "",
            searchedCharacters: []
        }
    },
    methods:{
        async searchByName(){
            const res =  await fetch(`https://rickandmortyapi.com/api/character/?name=${this.search}`)
            const data = await res.json()
            // console.log(data.results);
            this.searchedCharacters = data.results
            this.$emit('searchedCharacters', this.searchedCharacters)
        }
    }
}
</script>

<style>

</style>