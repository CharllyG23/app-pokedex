
import PokemonHeader from '../../components/PokemonHeader/PokemonHeader.vue';

<template>
  <header>
    <div class="header-logo">
         <h1>Pokedex</h1>
    </div>
    <a :href="gitHubUrl" target="_blank">Github</a>
  </header>
  <section>
    <div class="w-full py-20">
      <div class="max-w-screen-xl mx-auto  px-10">
        <div class="bg-white md:h-48 rounded-lg shadow-md flex flex-wrap flex-col-reverse md:flex-col">
          <div class="w-full md:w-1/2 p-6">
            <img src="https://www.mcdonalds.com/content/dam/usa/nfl/assets/nav/arches-logo_108x108.jpg" alt="" class="w-8">
            <h3 class="text-3xl font-bold">Fast Food & Cola</h3>
            <p>Get all your McDonald’s favorites delivered right to your doorstep with McDelivery® on Uber Eats or DoorDash.</p>
          </div>
          <div class="w-full md:w-1/2 p-4 md:p-0">
            <img :src="food" alt="" class="w-[400px] mx-auto">
          </div>
        </div>
      </div>
    </div>
  </section>
  <main>
    <pokemon-list></pokemon-list>
  </main>
</template>
<script setup>
import PokemonList from '../../components/PokemonList/PokemonList.vue';
import food from '../../assets/img/food.jpg'

const gitHubUrl = import.meta.env.VITE_APP_GITHUB_URL
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>