<template>
  <div class="content_planetas">
    <v-row>
      <v-row>
        <em>
          <br />
          <h1>Lista de Planetas</h1>
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
              src="https://castwars.com/wp-content/uploads/2013/02/Geonosis-1-.jpg"
              style="width: 800px; height: 400px"
            >
              <v-card-title>Geonosis</v-card-title>
            </v-img>

            <v-card-text>
              <div>
               <strong><em>Geonosis</em></strong> referido também como Geonosia por alguns nativos, foi o planeta natal dos Geonosianos. Um mundo inóspido e desértico, Geonosis foi a primeira capital...
              </div>
            </v-card-text>

            <v-card-action>
              <v-btn @click="vermais('primeiro_planeta')">Ver Mais</v-btn>
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
              src="https://cdnb.artstation.com/p/marketplace/presentation_assets/000/692/617/large/file.jpg?1611446119"
              style="width: 800px; height: 400px"
            >
              <v-card-title>Naboo</v-card-title>
            </v-img>

            <v-card-text>
              <div>
                Uma joia brilhante na Orla Média, <strong><em>Naboo</em></strong
                > tinha renome em toda a galáxia como um centro de paz e
                aprendizado. Suas belas cidades coexistiam em harmonia com as
                planícies...
              </div>
            </v-card-text>

            <v-card-action>
              <v-btn @click="vermais('segundo_planeta')">Ver Mais</v-btn>
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
              src="https://i.ytimg.com/vi/JdwbNSPs-9A/maxresdefault.jpg?sqp=-oaymwEmCIAKENAF8quKqQMa8AEB-AHUBoAC4AOKAgwIABABGGUgZShlMA8=&rs=AOn4CLA5yzjqJgQE_KNvCzh5fGkYQgK4fQ"
              style="width: 800px; height: 400px"
            >
              <v-card-title>Coruscant</v-card-title>
            </v-img>

            <v-card-text>
              <div>
                <strong><em>Coruscant</em></strong> foi um planeta que serviu
                como capital da República Galáctica e do Império Galáctico e
                como planeta natal da espécie humana...
              </div>
            </v-card-text>

            <v-card-action>
              <v-btn @click="vermais('terceiro_planeta')">Ver Mais</v-btn>
            </v-card-action>
          </v-card>
        </v-col>
      </v-row>
    </v-row>
    <v-dialog max-width="500" v-model="show_modal">
      <v-card title="História">
        <v-card-text>
          {{ texto_modal }}
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn text="Fechar" @click="show_modal = false"></v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>
   
  <script setup>
import { ref, useTemplateRef, onMounted } from "vue";

const texto_modal = ref("");
const show_modal = ref(false);

const vermais = (pl) => {
  if (pl == "primeiro_planeta") {
    texto_modal.value =
      "Geonosis, referido também como Geonosia por alguns nativos, foi o planeta natal dos Geonosianos. Um mundo inóspido e desértico, Geonosis foi a primeira capital da Confederação de Sistemas Independentes, tendo dentro de si um fábrica de droides de batalha. Foi o local da Primeira Batalha de Geonosis, o conflito que abriu as portas para as Guerras Clônicas, assim como a próxima invasão pela República Galáctica.";
  }
  if (pl == "segundo_planeta") {
    texto_modal.value =
      "Uma joia brilhante na Orla Média, Naboo tinha renome em toda a galáxia como um centro de paz e aprendizado. Suas belas cidades coexistiam em harmonia com as planícies gramadas e as colinas que as cercavam. O clima era temperado, e os predadores mais perigosos eram relegados, principalmente, ao peculiar núcleo aquático de Naboo. Ao contrário da maioria dos planetas que possuíam núcleos de lava, Naboo era vazado e preenchido com oceanos que correm em seu centro. E, nessas águas profundas, eram encontrados os ferozes Sando Aqua e Assassino Marítimo Opee.";
  }

  if (pl == "terceiro_planeta") {
    texto_modal.value =
      "Coruscant foi um planeta que serviu como capital da República Galáctica e do Império Galáctico e como planeta natal da espécie humana.O planeta-cidade Coruscant foi o coração pulsante da galáxia, abrigando uma diversidade de cidadãos e culturas. Tinha altíssimas torres de edifícios, fluxos de tráfego aéreo cheios de speeders e níveis internos que se estendiam muito abaixo da superfície do planeta. Coruscant foi a sede do governo da República Galáctica e, posteriormente, do Império, e foi palco de inúmeros eventos históricos durante as Guerras Clônicas.";
  }
  show_modal.value = true;
};

</script>