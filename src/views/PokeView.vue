<script setup>
import axios from "axios";
import { ref } from "vue";
import { useGetData } from "@/composables/getData";
import { useRoute, useRouter } from "vue-router";
import { useFavoritoStore } from "@/store/favoritos";
const route = useRoute();
const router = useRouter();
const pokeSprite = ref({});
const useFavorito = useFavoritoStore();

const back = () => {
    router.push("/pokemons");
};
const { add, findPoke } = useFavorito;

const { data, error, loading, getData } = useGetData(
    `https://pokeapi.co/api/v2/pokemon/${route.params.name}`
);

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>

<template>
    <main class="text-center">
        <div v-if="data">
            <img :src="data.sprites?.front_default" alt="" />
            <h1>Poke: {{ $route.params.name }}</h1>
            <button
                :disabled="findPoke(data.name)"
                @click="add(data)"> Agregar a Favoritos
            </button>
        </div>
        <h1 v-else>Pokemon no encontrado...</h1>
        <button @click="back()">Volver al listado</button>
    </main>
</template>
