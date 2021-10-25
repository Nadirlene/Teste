<template>
  <v-container class="content grey lighten-5">
    <v-row>
      <v-col cols="12">
        <v-row>
          <v-col :cols="larguraColunaTitulo">
            <v-row>
              <h2>{{ titulo }}</h2>
              <label>{{ subtitle }}</label>
            </v-row>
          </v-col>
          <v-col :cols="larguraColunaMedia">
            <v-media
              :texto="texto"
              :valor="valor"
              :porcentagem="porcentagem"
              :tipoTexto="tipoTextoMedia"
            ></v-media>
          </v-col>
        </v-row>
      </v-col>
    </v-row>

    <v-main class="modulos px-0 py-0 mb-5">
      <v-row>
        <v-col
          :cols="larguraColunacard"
          v-for="(item, index) in objetoFor"
          :key="index"
        >
          <v-card-info
            :altura="'130px'"
            :descricao="item.descricao"
            :porcentagem="item.porcentagem"
            :valor="item.valor"
            :data="item.data"
            :qtdAulas="item.qtdAulas"
          >
          </v-card-info>
        </v-col>
      </v-row>
    </v-main>
  </v-container>
</template>

<script>
import cardInformativo from "@/components/card_informativo/index.vue";
import media from "@/components/media/index.vue";
export default {
  props: {
    titulo: String,
    subtitle: String,
    porcentagem: String,
    valor: Number,
    objetoFor: Array,
    larguraColunacard: Number,
    larguraColunaTitulo: Number,
    larguraColunaMedia: Number,
  },
  components: {
    "v-media": media,
    "v-card-info": cardInformativo,
  },
  data: () => ({
    texto: "Média de Módulos",
    tipoTextoMedia: true,
  }),
};
</script>

<style scoped>
h2 {
  padding-left: 15px;
  padding-right: 15px;
  margin-top: 15px;
}

label {
  margin-top: 20px;
  padding-left: 40px;
}

main.v-main.modulos {
  padding: 0;
}

@media (max-width: 1320px) {
  .div-col-md-4 {
    display: flex;
    flex-direction: row;
  
  }
}
</style>

