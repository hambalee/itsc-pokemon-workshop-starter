<script setup lang="ts">
import { useRoute, useRouter } from "vue-router";
import { getPokemonByName } from "@/services/pokemon.service";
import { ref } from "vue";
import type { PokemonDetailData } from "@/models/pokemon.model";

const router = useRouter();

const route = useRoute();

const pokemonName = route.params.name;

const pokemon = ref<PokemonDetailData>();

getPokemonByName(pokemonName.toString()).then(
  (value) => (pokemon.value = value)
);

const onNavigateBack = () => router.back();
</script>

<template>
  <button class="btn btn-link" @click="onNavigateBack">Back</button>
  <div>
    {{ pokemon }}
  </div>
</template>
