<template> 
    <v-row>
    <v-col cols=3 v-for="personagem in resourcePersonagens" :key="personagem.name">
      <v-card>{{ personagem.name }} - {{ personagem.birth_year }}</v-card>
    </v-col>
</v-row>
</template>
<script setup>
import { ref, useTemplateRef, onMounted } from "vue";
const resourcePersonagens = ref([])

onMounted(async()=>{

  const url = "https://swapi.dev/api/people";
  
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const json = await response.json();
    console.log(json);
    resourcePersonagens.value = json.results
  } catch (error) {
    console.error(error.message);
  }

})
</script>