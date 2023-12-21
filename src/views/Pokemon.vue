<script setup>
import { useRoute } from "vue-router";
import usePokemons from "@/composables/pokemon";

//Get the id in the URL
const route = useRoute();
const id = route.params.id;

//Fetch the data with the id (Axios)
const { data } = usePokemons(id);
console.log(data);

//Remplace les premières lettres par des majuscules
const capitalizeFirstLetter = (word) => {
  return word.charAt(0).toUpperCase() + word.slice(1);
};

// Remplace tous les underscores par des espaces
const formatStatName = (statName) => {
  return statName.replace(/_/g, " ");
};
</script>

<template>
  <div
    class="flex flex-col justify-center w-full bg-gradient-to-br from-indigo-900 via-teal-500 to-cyan-400 h-screen"
  >
    <div v-if="data" class="mx-auto w-96">
      <h1 class="text-xl">{{ data.name }}</h1>
      <img :src="data.image" alt="pokemon" />

      <div v-if="data.stats">
        <div
          class="flex items-center justify-between mt-4"
          v-for="(value, statName) in data.stats"
          :key="statName"
        >
          <div class="w-32">
            {{ capitalizeFirstLetter(formatStatName(statName)) }} :
          </div>
          <div class="flex items-center w-64">
            <div class="bg-gray-200 h-5 w-48 rounded-full">
              <div
                :class="{
                  'bg-green-600': value >= 90,
                  'bg-yellow-500': value >= 60 && value < 90,
                  'bg-red-500': value < 60,
                }"
                :style="{ width: value + 'px' }"
                class="h-full rounded-full"
              ></div>
            </div>
            <div>{{ value }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
