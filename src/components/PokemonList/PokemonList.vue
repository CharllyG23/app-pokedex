<template>
  <div class="pokemonList">
    <div class="pokemonList_container">
     <div class="pokemonList_content">
      <pokemon-card v-for="(item, index) in pokemons.results" :key="index" :data="item" />
     </div>
    </div>
  </div>
</template>
<script setup>
import { onMounted, ref } from 'vue';
import PokemonCard from '../PokemonCard/PokemonCard.vue';
import api from '../../support/http/api'

const pokemons = ref({})
const pokemonId = ref('')

const getPokemon = async () => {
  try{
    const url = `${pokemonId}`
    const response = await api.get(url)
    pokemons.value = response.data
    console.log('Respuesta',response)
  }catch (error) {
    console.error(error);
  }
}

onMounted(() =>{
  getPokemon()
})
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>