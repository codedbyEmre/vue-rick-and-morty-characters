<template>
  <div class="character-container border border-4 border-white rounded m-3" v-for="(character,index) in characters" :key="index" data-bs-toggle="modal" data-bs-target="#showCharacterModal" @click="openCharacterModal(index)">
      <img :src="character.image" :alt="character.name">
      <h3>{{character.name}}</h3>
  </div>


    <!-- Show Character Modal -->
    <div class="modal fade" id="showCharacterModal" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="staticBackdropLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="staticBackdropLabel">Character Details</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <div class="row">
                    <div class="col-sm-6">
                        <p>Name: {{name}}</p>
                        <p>Gender: {{gender}}</p>
                        <p>Status: {{status}}</p>
                        <p>Species: {{species}}</p>
                        <p>Location: {{location}}</p>
                        <p>Origin: {{origin}}</p>
                    </div>
                    <div class="col-sm-6">
                        <img :src="image" :alt="name" class="img-fluid rounded">
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-outline-secondary" data-bs-dismiss="modal">Close</button>
            </div>
        </div>
    </div>
    </div>


</template>

<script>
export default {
    name: "Characters",
    props: ["characters"],
    data(){
        return{
            name: "",
            gender: "",
            status: "",
            species: "",
            location: "",
            origin: "",
            image: ""
        }
    },
    methods: {
        openCharacterModal(index){
            // console.log(this.characters[index]);
            this.name = this.characters[index].name
            this.gender = this.characters[index].gender
            this.status = this.characters[index].status
            this.species = this.characters[index].species
            this.location = this.characters[index].location.name
            this.origin = this.characters[index].origin.name
            this.image = this.characters[index].image
        }
    }
}
</script>

<style>

</style>