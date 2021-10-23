<template>
  <v-container class="content mx-auto ">
    <v-row>
      <v-col cols="1" md="1">
        <v-btn text><v-icon>mdi-arrow-left</v-icon></v-btn>
        <v-icon>mdi-school</v-icon>
      </v-col>

      <v-col cols="4" md="4">
        <h3>{{ nome }}</h3>
        <p class="caption">{{ email }}</p>
      </v-col>

      <v-col cols="3" md="4">
        <p class="subtitle-2 mb-0">Primeiro Acesso</p>
        <p class="caption">{{ primeiroAcesso }}</p>
      </v-col>

      <v-col cols="3" md="4">
        <p class="subtitle-2 mb-0">Último Acesso</p>
        <p class="caption">{{ ultimoAcesso }}</p>
      </v-col>

      <v-col cols="4" md="4">
        <v-media
          :texto="texto"
          :valor="valor"
          :porcentagem="porcentagem"
        ></v-media>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import media from "@/components/media/index.vue";
export default {
  props: {
    nome: String,
    email: String,
    primeiroAcesso: String,
    ultimoAcesso: String,
    porcentagem: String,
    valor: Number,
  },
  components: {
    "v-media": media,
  },
  data: () => ({
    texto: "Média Geral",
  }),
};
</script>

<style scoped>
.col-md-4 {
  flex: 0 0 20%;
  max-width: 20%;
}

@media (max-width: 960px) {
  .col-md-4 {
    flex: 0 0 50%;
    max-width: 50%;
  }
}

@media (max-width: 760px) {
  .col-md-4 {
    flex: 0 0 100%;
    max-width: 100%;
  }
}
</style>

