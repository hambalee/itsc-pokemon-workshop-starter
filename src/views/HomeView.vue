<script setup lang="ts">
import PokemonCard from "@/components/PokemonCard.vue";
import type { PokemonData } from "@/models/pokemon.model";
import { getPokemons } from "@/services/pokemon.service";
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

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
  </div>
</template>
