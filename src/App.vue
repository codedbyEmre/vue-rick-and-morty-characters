<template>
  <Header />
  <div class="d-flex justify-content-center align-items-center mt-5 px-3">
    <Search @searchedCharacters="searchedCharacters($event)"/>
  </div>
  <div class="container-md d-flex flex-wrap justify-content-center my-5">
    <Characters :characters="characters"/>
  </div>
  <div class="d-flex justify-content-center mb-5">
    <div class="btn-group" role="group" aria-label="Basic example">
      <button type="button" class="btn btn-success btn-lg" @click="prevPage">Prev</button>
      <button type="button" class="btn btn-success btn-lg" @click="nextPage">Next</button>
    </div>
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Search from './components/Search.vue'
import Characters from './components/Characters.vue'

export default {
  name: 'App',
  components: { Header, Search, Characters },
  data(){
    return{
      characters: [],
      currentPage: 1,
      totalPages: 0
    }
  },
  methods: {
    async getCharacters(){
      const res = await fetch(`https://rickandmortyapi.com/api/character`)
      const data = await res.json()

      // console.log(data.info);
      this.totalPages = data.info.pages
      // console.log(data.results);

      this.characters = data.results
    },
    searchedCharacters(characters){
      this.characters = characters
    },
    async prevPage(){
      // console.log(this.currentPage);
      if(this.currentPage > 1){
        this.currentPage--
        const res = await fetch(`https://rickandmortyapi.com/api/character/?page=${this.currentPage}`)
        const data = await res.json()
        this.characters = data.results
      }
    },
    async nextPage(){
      // console.log(this.currentPage);
      if(this.currentPage < this.totalPages){
        this.currentPage++
        const res = await fetch(`https://rickandmortyapi.com/api/character/?page=${this.currentPage}`)
        const data = await res.json()
        this.characters = data.results
      }
    }
  },
  created(){
    this.getCharacters()
  }
}
</script>

<style>
</style>
