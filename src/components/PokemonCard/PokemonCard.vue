<template>
  <div class="pokemonCard">
    <div class="pokemonCard_image">
      <div class="pokemonCard_image_inner-skew">
        <!-- <img :src="data.sprites.id" alt="" class="w-full mx-auto" /> -->
      </div>
    </div>
    <div class="pokemonCard_content">
      <h3>{{ data.name }}</h3>
      <div>
        This a demo experiment to skew image container. It looks good.
      </div>
    </div>
  </div>
</template>
<script setup>
import food from '../../assets/img/food.jpg'

defineProps({
  data: { type: Object, required: true},
})
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>
