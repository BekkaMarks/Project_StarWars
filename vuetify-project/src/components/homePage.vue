<template>
  <div class="homepage">
    <h1>Seja bem-vindo(a), viajante!</h1>
    <v-row>
      <v-col cols="12" md="4" lg="3">
        <v-card>
          <v-img
            class="align-end text-white"
            :width="450"
            aspect-ratio="16/9"
            cover
            src="https://assets.b9.com.br/wp-content/uploads/2020/02/glb9.jpg"
          >
            <v-card-title>O gênio por trás da obra</v-card-title>
          </v-img>

          <v-card-subtitle class="pt-3">George Lucas</v-card-subtitle>

          <v-card-text>
            <div>
              O criador da saga Star Wars, baseou sua obra no conceito da
              Jornada do Herói de Joseph...
            </div>
          </v-card-text>

          <v-card-action>
            <v-btn @click="vermais('primeiro_card')">Ver Mais</v-btn>
          </v-card-action>
        </v-card>
      </v-col>

      <v-col cols="12" md="4" lg="3">
        <v-card>
          <v-img
            class="align-end text-white"
            :width="450"
            aspect-ratio="16/9"
            cover
            src="https://ichef.bbci.co.uk/ace/standard/976/cpsprodpb/91E8/production/_99125373_5fccea6c-98dc-48f0-beab-03b38a37f379.jpg"
          >
            <v-card-title>Tempo de produção</v-card-title>
          </v-img>

          <v-card-subtitle class="pt-3">Início em 1975</v-card-subtitle>

          <v-card-text>
            <div>
              A saga <em>Star Wars</em> começou a ser produzida em 1975, com o
              desenvolvimento do primeiro filme...
            </div>
          </v-card-text>

          <v-card-action>
            <v-btn @click="vermais('segundo_card')">Ver Mais</v-btn>
          </v-card-action>
        </v-card>
      </v-col>

      <v-col cols="12" md="4" lg="3">
        <v-card>
          <v-img
            class="align-end text-white"
            :width="450"
            aspect-ratio="16/9"
            cover
            src="https://www.hollywoodreporter.com/wp-content/uploads/2017/10/gettyimages-129042800_-_h_2017.jpg?w=1296&h=730&crop=1"
          >
            <v-card-title>Conquistas da trilogia</v-card-title>
          </v-img>

          <v-card-subtitle class="pt-3">Oscar</v-card-subtitle>

          <v-card-text>
            <div>
              Indicado ao oscar 23 vezes. O filme com maior indicações foi
              <strong>"Uma Nova Esperaça"</strong>...
            </div>
          </v-card-text>

          <v-card-action>
            <v-btn @click="vermais('terceiro_card')">Ver Mais</v-btn>
          </v-card-action>
        </v-card>
      </v-col>
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

    <v-col class="d-flex flex-column align-center" cols="0">
      <code>{{ code }}</code>
      <v-tooltip :location="location" :origin="origin" no-click-animation>
      </v-tooltip>
    </v-col>
    <v-col>
      <v-radio-group
        v-model="originAlign"
        label="Sabemos que a saga é repleta de personagens icônicos, mas agora é a sua vez, viajante! Entre as opções a seguir, qual deles é o seu favorito?"
      >
        <v-radio label="R2-D2" value="r2"></v-radio>
        <v-radio label="Darth Vader" value="darth_vader"></v-radio>
        <v-radio label="Han Solo" value="han_solo"></v-radio>
        <v-radio label="Yoda" value="yoda"></v-radio>
        <v-radio label="Boba Fett" value="boba_fett"></v-radio>
      </v-radio-group>
    </v-col>
  </div>
</template>

<script setup>
import { ref, useTemplateRef, onMounted } from "vue";
const texto_modal = ref("");
const show_modal = ref(false);

const vermais = (card) => {
  if (card == "primeiro_card") {
    texto_modal.value =
      "George Lucas, o criador da série Star Wars, se inspirou no conceito mitológico de Jornada do Herói de Joseph Campbell para criar a série. Produtor e roteirista americano, mais conhecido por criar a icônica franquia Star Wars e por fundar a Lucasfilm. Nascido em 14 de maio de 1944, em Modesto, Califórnia, Lucas se formou em cinema na Universidade da Califórnia, onde começou a desenvolver suas ideias inovadoras.Após dirigir o sucesso 'American Graffiti' em 1973, Lucas lançou 'Star Wars' em 1977, que revolucionou o cinema de ficção científica e se tornou um fenômeno cultural. A saga Star Wars, com suas histórias épicas, personagens memoráveis e efeitos especiais inovadores, se expandiu para se tornar uma das franquias mais lucrativas da história do entretenimento.Além de Star Wars, Lucas também criou a série Indiana Jones, em parceria com Steven Spielberg. Em 2012, ele vendeu a Lucasfilm para a Disney, permitindo que novas gerações experimentassem suas criações. Lucas é amplamente reconhecido por sua contribuição ao cinema, tanto em termos de narrativa quanto de tecnologia.";
  }

  if (card == "segundo_card") {
    texto_modal.value =
      "A saga Star Wars começou a ser produzida em 1975, com o desenvolvimento do primeiro filme, 'Uma Nova Esperança', que foi lançado em 1977. A série principal, composta por nove filmes, foi lançada ao longo de várias décadas, com o último da trilogia Skywalker, A Ascensão Skywalker, lançado em 2019. Assim, a produção da saga abrange um período de mais de 40 anos, considerando os filmes, séries e outros projetos relacionados.";
  }

  if (card == "terceiro_card") {
    texto_modal.value =
      "Indicado ao Oscar 23 vezes, o filme com mais indicações da franquia Star Wars foi 'Uma Nova Esperança', que concorreu em 6 categorias. O primeiro filme da saga conquistou sete estatuetas técnicas, incluindo a de efeitos sonoros. 'O Império Contra-Ataca', lançado em 1981, recebeu mais duas estatuetas, enquanto 'O Retorno de Jedi', o fechamento da trilogia original, lançado em 1984, levou uma.";
  }
  show_modal.value = true;
};

const originAlign = ref("bottom");
</script>