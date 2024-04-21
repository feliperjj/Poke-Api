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
    <strong>Game Indices:</strong>   
    <span>{{pokemon.game_indices}}</span>  
     
     </section>
    
       <section class="col">
    <strong>moves:</strong>   
    <span>{{pokemon.moves}}</span>  
     
    
     </section>
      
    
    </div>
    

  </div>
</div>

</template>

<style scoped>
.CardPokemonSelected{
    height: 75vh;
    background: rgb(72,63,251);
    background: radial-gradient(circle, rgba(220, 194, 106, 0.8) 0%, rgba(244, 0, 0, 0.8) 100%);
}
.CardPokemonSelected img{
    height: 250px;
}

@media (max-width: 768px) {
    .CardPokemonSelected{
        height: 30vh;
        width: 40%;
        margin: 0 auto 10px auto;
    }
    .CardPokemonSelected img{
        height: 100px;
    }
}
</style>