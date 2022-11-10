<script setup>
import { useFavoritoStore } from "../store/favoritos";
import { storeToRefs } from "pinia";

const useFavorito = useFavoritoStore();

const { favoritos } = storeToRefs(useFavorito);
const { remove } = useFavorito;
</script>

<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos.length === 0">Sin favoritos</p>
    <div v-else v-for="poke in favoritos" :key="poke.id">
      <img :src="poke.sprites?.front_default" alt="">
      <span> {{ poke.name }}</span>
      <router-link
          class="btn btn-sm btn-outline-primary me-2"
          :to="`/pokemons/${poke.name}`"
      >
          Más info
      </router-link>
      <button
          class="btn btn-sm btn-outline-danger"
          @click="remove(poke.id)"
      >
          Eliminar
      </button>
    </div>
</template>
