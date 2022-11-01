<script setup lang="ts">
import PokemonCard from "@/components/MyPokemonCard.vue";

import type { PokemonData } from "@/models/pokemon.model";
import { ref } from "vue"; // useState in react
import { getPokemons } from "@/services/pokemon.service";
import { useRouter } from "vue-router";

const router = useRouter();

// const myName = ref("Lee");

// const pokemon = ref<PokemonData>({
//   name: "Pikachu",
//   img: "https://picsum.photos/id/237/200/300",
// });

const pokemons = ref<PokemonData[]>([]);

getPokemons().then((value) => (pokemons.value = value));
const onViewDetail = (name: string) => {
  router.push({ name: "detail", params: { name: name } });
};
</script>

<template>
  <div class="container mw-[1024px] mx-auto">
    <PokemonCard
      v-for="pokemon of pokemons"
      :key="pokemon.name"
      :name="pokemon.name"
      :img="pokemon.img"
      @view-detail="onViewDetail"
    ></PokemonCard>
    <div class="text-center text-4xl">Welcome to Pokemon workshop !</div>
    <!-- <div>My name is {{ myName }}</div> -->
  </div>
</template>
