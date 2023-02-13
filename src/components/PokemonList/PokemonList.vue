<template>
  <div class="pokemonList">
    <div class="pokemonList_container">
     <div class="pokemonList_content">
      <pokemon-card v-if="Object.keys(search).length" :data="search" />
      <template v-else>
        <pokemon-card v-for="(item, index) in pokemons.results" :key="index" :data="item" />
      </template>
     </div>
    </div>
  </div>
</template>
<script setup>
import { onMounted, ref } from 'vue';
import PokemonCard from '../PokemonCard/PokemonCard.vue';
import api from '../../support/http/api'

const props = defineProps({
  search: { type: Object, default: {} }
})

const pokemons = ref({})

const getPokemonList = async () => {
  try{
    const response = await api.get()
    pokemons.value = response.data
  }catch (error) {
    console.error(error);
  }
}

onMounted(() =>{
  getPokemonList()
})
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>