<template>
  <section class="banner">
    <div class="banner_container">
      <div class="banner_container_content">
        <div class="info">
          <div class="info_header">
            <h3 class="info_header__title">Sua pokedéx oficial.</h3>
            <p class="info_header__subTitle">Aqui você encontra todos os pokémons que quiser!</p>
            <!-- <a :href="gitHubUrl" target="_blank" class="info_header__subTitle pt-6">Github</a> -->
          </div>
          <div class="info_image">
            <img :src="pikachu" alt="pikachu" />
          </div>
        </div>
      </div>
    </div>
  </section>
  <section>
    <pokemon-search @search-pokemon="setSearchPokemon"></pokemon-search>
  </section>
  <main>
    <pokemon-list :search="searchPokemon"></pokemon-list>
  </main>
</template>
<script setup>
import { ref } from 'vue'
import PokemonList from '../../components/PokemonList/PokemonList.vue';
import PokemonSearch from '../../components/PokemonSearch/PokemonSearch.vue';
import pikachu from '../../assets/img/pikachu.png'

const gitHubUrl = import.meta.env.VITE_APP_GITHUB_URL
const searchPokemon = ref({})

const setSearchPokemon = (data) => {
  searchPokemon.value = data
}
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>