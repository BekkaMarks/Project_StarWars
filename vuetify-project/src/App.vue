<template>
  <v-app>
    <v-navigation-drawer v-model="isDrawerOpen">
      <v-card>
        <v-layout>
          <v-navigation-drawer
            image="https://i.pinimg.com/736x/f3/c5/db/f3c5db295466abbcee9ada5b3c77c33b.jpg"
            theme="dark"
            permanent
          >
            <v-list nav>
              <v-list-item
                prepend-icon="mdi-home-circle"
                @click="click_pagina('home')"
                title="Home"
                value="principal"
              ></v-list-item>
              <v-list-item
                prepend-icon="mdi-robot-happy"
                @click="click_pagina('personagens')"
                title="Personagens"
                value="personagem"
              ></v-list-item>
              <v-list-item
                prepend-icon="mdi-death-star-variant"
                title="Planetas"
                @click="click_pagina('planetas')"
                value="planeta"
              ></v-list-item>
              <v-list-item
                prepend-icon="mdi-api"
                title="API"
                @click="click_pagina('api')"
                value="api"
              ></v-list-item>
            </v-list>
          </v-navigation-drawer>
          <v-main style="height: 910px"></v-main>
        </v-layout>
      </v-card>
    </v-navigation-drawer>
    <v-app-bar flat class="border-b">
      <template v-slot:prepend>
        <v-app-bar-nav-icon
          @click="isDrawerOpen = !isDrawerOpen"
        ></v-app-bar-nav-icon>
      </template>
      <v-row class="ml-2">
        <v-col cols="6" sm="3" md="3" lg="6">
          <v-text-field
            label="Pesquisa"
            prepend-icon="mdi-magnify"
            variant="underlined"
          ></v-text-field>
        </v-col>
      </v-row>

      <v-app-bar
        scroll-behavior="fade-image"
        scroll-threshold="71"
        image="https://i.pinimg.com/originals/60/e0/39/60e03966cb9e44a3462d81742dbaf287.jpg"
      >
      </v-app-bar>

      <template #append>
        <v-menu>
          <template v-slot:activator="{ props }">
            <v-avatar v-bind="props">
              <v-img
                src="https://castwars.com/wp-content/uploads/2017/12/blogmedia-17200.jpg"
              >
              </v-img>
            </v-avatar>
          </template>

          <v-list>
            <v-list-item v-for="(item, i) in itens" :key="i">
              <v-list-item-title @click="teste(item.name)">{{
                item.title
              }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </template>
    </v-app-bar>

    <v-main>
      <v-container>
        <homePage v-if="view_page == 'home'" />

        <v-row v-if="view_page == 'personagens'">
          <v-row>
            <em>
              <br>
              <h1>Vamos conhecer alguns dos personagens</h1>
            </em>
          </v-row>
          <v-row>
            <v-col cols="12" md="4" lg="3">
              <v-card>
                <v-img
                  class="align-stretch text-white"
                  :width="450"
                  aspect-ratio="16/9"
                  cover
                  src="https://nsabers.es/cdn/shop/articles/celehey_Anakin_Skywalker_wielding_blue_lightsaber_defeats_chanc_78152037-5543-4d57-9b68-8829daa3f9ee.png?v=1708935727"
                  style="width: 800px; height: 400px"
                >
                  <v-card-title>Anakin Skywalker</v-card-title>
                </v-img>

                <v-card-text>
                  <div>
                    <strong><em>Anakin Skywalker</em></strong> foi um lendário
                    Cavaleiro Jedi que serviu a República Galáctica durante seus
                    últimos anos, e mais tarde se tornou...
                  </div>
                </v-card-text>

                <v-card-action>
                  <v-btn @click="vermais('primeiro_personagem')"
                    >Ver Mais</v-btn
                  >
                </v-card-action>
              </v-card>
            </v-col>
            <v-col cols="12" md="4" lg="3">
              <v-card>
                <v-img
                  class="align-stretch text-white"
                  :width="450"
                  aspect-ratio="16/9"
                  cover
                  src="https://images4.alphacoders.com/132/1327480.png"
                  style="width: 800px; height: 400px"
                >
                  <v-card-title>Darth Vader</v-card-title>
                </v-img>

                <v-card-text>
                  <div>
                    No episódio I da nova trilogia, Anakin Skywalker (interpretado por Jake Lloyd), o futuro <strong><em> Darth Vader</em></strong>, com nove anos de idade...
                  </div>
                </v-card-text>

                <v-card-action>
                  <v-btn @click="vermais('segundo_personagem')">Ver Mais</v-btn>
                </v-card-action>
              </v-card>
            </v-col>
            <v-col cols="12" md="4" lg="3">
              <v-card>
                <v-img
                  class="align-stretch text-white"
                  :width="450"
                  aspect-ratio="16/9"
                  cover
                  src="https://images4.alphacoders.com/135/1353792.png"
                  style="width: 800px; height: 400px"
                >
                  <v-card-title>Boba Fett</v-card-title>
                </v-img>

                <v-card-text>
                  <div>
                    <strong><em>Boba Fett</em></strong> foi um clone inalterado de Jango Fett, um homem caçador de recompensas Mandaloriano que criou Boba como seu 
                  </div>
                </v-card-text>

                <v-card-action>
                  <v-btn @click="vermais('terceiro_personagem')"
                    >Ver Mais</v-btn
                  >
                </v-card-action>
              </v-card>
            </v-col>
          </v-row>
        </v-row>

        <PlanetPage v-if="view_page == 'planetas'"/>
        <ApiPage v-if="view_page == 'api'"/>
        
  
  
        <v-dialog max-width="500" v-model="show_ml">
          <v-card title="História">
            <v-card-text>
              {{ texto_ml }}
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>

              <v-btn text="Fechar" @click="show_ml = false"></v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        
      </v-container>
    </v-main>
  </v-app>
</template>
 
<script setup>
import { ref, useTemplateRef, onMounted } from "vue";

import homePage from "./components/homePage.vue";

import PlanetPage from "./components/PlanetPage.vue";

import Sabre from "./components/Sabre.vue";

import ApiPage from "./components/ApiPage.vue";

const isDrawerOpen = ref(false);
const itens = ref([
  { title: "Perfil", name: "perfil" },
  { title: "Configurações", name: "config" },
  { title: "Sair", name: "sair" },
]);

const teste = (id) => {
  if (id == "sair") {
    window.location.reload(true);
  }
};

const click_pagina = (page) => {
  view_page.value = page;
  isDrawerOpen.value = false;
};

const texto_ml = ref("");
const show_ml = ref(false);

const vermais = (tx) => {
  if (tx == "primeiro_personagem") {
    texto_ml.value =
      "George Lucas, o criador da série Star Wars, se inspirou no conceito mitológico de Jornada do Herói de Joseph Campbell para criar a série. Produtor e roteirista americano, mais conhecido por criar a icônica franquia Star Wars e por fundar a Lucasfilm. Nascido em 14 de maio de 1944, em Modesto, Califórnia, Lucas se formou em cinema na Universidade da Califórnia, onde começou a desenvolver suas ideias inovadoras.Após dirigir o sucesso 'American Graffiti' em 1973, Lucas lançou 'Star Wars' em 1977, que revolucionou o cinema de ficção científica e se tornou um fenômeno cultural. A saga Star Wars, com suas histórias épicas, personagens memoráveis e efeitos especiais inovadores, se expandiu para se tornar uma das franquias mais lucrativas da história do entretenimento.Além de Star Wars, Lucas também criou a série Indiana Jones, em parceria com Steven Spielberg. Em 2012, ele vendeu a Lucasfilm para a Disney, permitindo que novas gerações experimentassem suas criações. Lucas é amplamente reconhecido por sua contribuição ao cinema, tanto em termos de narrativa quanto de tecnologia.";
  }
  if (tx == "segundo_personagem") {
    texto_ml.value =
      "No episódio I da nova trilogia, Anakin Skywalker (interpretado por Jake Lloyd), o futuro Darth Vader, com nove anos de idade, é um escravo que vive com sua mãe Shmi Skywalker, em Tatooine – planeta deserto do universo Star Wars. Era um menino prodígio, talentoso piloto de “pods”. É então descoberto pelo mestre Jedi Qui-Gon Jinn, depois que esse fez um pouso de emergência em Tatooine. Ao perceber o talento do jovem, se convence que ele é o “escolhido da profecia Jedi”, que derrotará os Sith e trará o equilíbrio para a Força.";
  }

  if (tx == "terceiro_personagem") {
    texto_ml.value =
      "Boba Fett foi um clone inalterado de Jango Fett, um homem caçador de recompensas Mandaloriano que criou Boba como seu filho durante a Era da República. Fett imitou seu doador genético, a quem ele considerava seu pai, ao usar uma armadura Mandaloriana personalizada. Sua espaçonave pessoal era a Escravo I, uma nave de patrulha classe 31 Firespray-31 que pertenceu a Jango. Treinado em combate e habilidades marciais desde jovem, Fett foi um dos caçadores de recompensas mais temidos da galáxia durante a Era do Império. Ele se tornou uma lenda ao longo de sua carreira, que incluiu contratos para o Império Galáctico e o extenso submundo do crime.";
  }
  show_ml.value = true;
};

const view_page = ref("home");

</script>
