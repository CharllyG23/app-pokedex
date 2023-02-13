<template>
  <div class="pokemonCard">
    <div class="pokemonCard_content" @click="openModal">
      <div class="image">
        <img v-if="!loading" :src="pokemon.sprites.front_default" alt="pokemon" width="105" />
      </div>
      <h3 class="title">{{formatString(data.name) }}</h3>
      <div class="types">
        <div v-for="(type, index) in pokemon.types" :key="index">
          <span class="bg-gray-100 rounded-md px-3 py-1 text-slate-700">{{formatString( type.type.name )}} </span>
        </div>
      </div>
    </div>
  </div>
  <pokemon-details v-model="isActive" :info="pokemon"></pokemon-details>
</template>
<script setup>
import { onMounted, ref, watch } from 'vue'
import  api from '../../support/http/api.js'
import PokemonDetails from '../PokemonDetails/PokemonDetails.vue';

const props = defineProps({
  data: { type: Object, required: true},
})

const isActive = ref(false)
const pokemon = ref({})
const loading = ref(true)

const formatString = (str) => {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

const getPokemon = async () => {
  try{
    const pokemonName = props.data.name
    const response = await api.get(pokemonName)
    pokemon.value = response.data
    loading.value = false
  }catch (error) {
    console.error(error);
  }
}

const openModal = () =>{
  isActive.value = true
}

watch(() => props.data, async () => {
  loading.value = true
  await getPokemon()
})

onMounted(() =>{
  getPokemon()
})
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>
