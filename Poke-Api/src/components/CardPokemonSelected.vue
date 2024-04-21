<script setup>
const pokemon = defineProps(["name","xp","game_indices","moves","img"])

</script>
<template>
 <div class="card CardPokemonSelected">
  <img v-if="pokemon.name" :src="pokemon.img" height="200" class="card-img-top" :alt="pokemon.name">
    <img v-else src="../assets/egg_pokemon.svg" height="200" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title text-center">{{pokemon.name || '???'}}</h5>
    <hr>
    <div class="row">
     <section class="col">
    <strong>XP:</strong>   
    <span>{{pokemon.xp}}</span>  
     
     </section>
       <section class="col">
    <strong>Game Indices: </strong>   
    <span class="game-indices">{{pokemon.game_indices}}</span>  
     
     </section>
    
       <section class="col">
    <strong>Moves: </strong>   
    <span class="moves">{{pokemon.moves}}</span>  
     
    
     </section>
     
      
    
    </div>
    

  </div>
</div>

</template>

<style scoped>
.CardPokemonSelected{
    min-height: 75vh; /* Use min-height instead of height */
    background: rgb(72,63,251);
    background: radial-gradient(circle, rgba(220, 194, 106, 0.8) 0%, rgba(244, 0, 0, 0.8) 100%);
}
.CardPokemonSelected img{
    height: 250px;
    width: auto; /* Add this to maintain aspect ratio */
}

.moves {
  color: black; 
  font-weight: bold; 
}

.game-indices {
  color: #black; 
  font-weight: bold; 
  font-style: italic;
}

@media (max-width: 768px) {
    .CardPokemonSelected{
        min-height: 30vh; 
        width: 100%; 
        margin: 0 auto 10px auto;
    }
    .CardPokemonSelected img{
        height: auto;
        max-width: 100%; 
    }
}
</style>
