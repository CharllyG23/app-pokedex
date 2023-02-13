<template>
  <div class="pokemonCard">
    <div class="pokemonCard_content">
      <div class="image">
        <img v-if="!loading" :src="pokemon.sprites.front_default" alt="pokemon" width="105" />
      </div>
      <h3 class="title">{{ data.name }}</h3>
      <div class="types">
        <div v-for="(type, index) in pokemon.types" :key="index">
          <span>{{ type.type.name }} </span>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { computed, onMounted, ref, watch } from 'vue'
import  api from '../../support/http/api.js'

const props = defineProps({
  data: { type: Object, required: true},
})

const pokemon = ref({})
const loading = ref(true)

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
