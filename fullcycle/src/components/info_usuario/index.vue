<template>
  <v-row >
    <v-col cols="2" md="2" sm="12" >
      <v-btn text><v-icon>mdi-arrow-left</v-icon></v-btn>
      <v-icon  class="icons">mdi-school</v-icon>
    </v-col>

    <v-col cols="2" md="3" sm="12">
      <h3>{{ nome }}</h3>
      <p class="caption mb-0">{{ email }}</p>
    </v-col>

    <v-col cols="2" md="2" sm="12">
      <p class="subtitle-2 font-weight-bold pt-2 mb-0">Primeiro Acesso</p>
      <p class="caption mb-0">{{ primeiroAcesso }}</p>
    </v-col>

    <v-col cols="2" md="2" sm="12">
      <p class="subtitle-2 font-weight-bold pt-2 mb-0">Último Acesso</p>
      <p class="caption mb-0">{{ ultimoAcesso }}</p>
    </v-col>

    <v-spacer></v-spacer>
    <v-col cols="3" md="3" sm="12">
      <v-media
        :texto="texto"
        :valor="valor"
        :porcentagem="porcentagem"
        :tipoTexto="tipoTextoMedia"
      ></v-media>
    </v-col>
  </v-row>
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
    tipoTextoMedia: true,
  }),
};
</script>

<style scoped>

  .icons {
   float: right;
  }

@media(max-width: 600px){

  .col-sm-12{
    flex: 0 0 100%;
    max-width: 100%;
    padding-left:5%;
  }
}


</style>

