<template>
    <div class="pokemonSearch">
        <div class="pokemonSearch_container" >   
            <div class="pokemonSearch_container__input">
                <div class="svg">
                    <svg aria-hidden="true" class="w-5 h-5 text-gray-500 dark:text-gray-400" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd"></path></svg>
                </div>
                <input 
                    v-model="searchText" 
                    type="text" 
                    id="simple-search"  
                    :class="{ 'bg-red-300': error }" 
                    class="input"
                    placeholder="Search pokemon" 
                    required 
                />
            </div>
            <button @click.prevent="search" type="submit" class="pokemonSearch_container__button">
                Busca
            </button>
        </div>
        <span class="error" v-if="error">Porfavor escreve de novo</span>
    </div>
</template>
<script setup>
import { ref, watch } from 'vue'
import  api from '../../support/http/api.js'

const searchText = ref('')
const emit = defineEmits('searchPokemon')
const error = ref(false)

const search = async () => {
    await api.get(searchText.value).then((response)=>{
        emit('searchPokemon', response.data)
        console.log('Respuesta search', response)
    }).catch((err)=>{
        console.log(err)
        error.value = true
    })
}

watch(() => searchText.value, async () => {
    error.value = false
})

</script>
<style lang="scss" scoped>
@import './style.scss';
</style>>