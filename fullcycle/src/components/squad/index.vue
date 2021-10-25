<template>
  <v-container class="content grey lighten-5">
    <v-row>
      <v-col cols="12">
        <h4>{{ titulo }}</h4>
        <label>{{ subtitle }}</label>
        <v-media
          :texto="texto"
          :valor="valor"
          :porcentagem="porcentagem"
        ></v-media>
      </v-col>
    </v-row>
    
    <v-card-info
      v-for="(item, index) in objetoFor"
      :key="index"
      :descricao="item.descricao"
      :porcentagem="item.porcentagem"
      :valor="item.valor"
      :data="item.data"
    >
    </v-card-info>
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
  },
  components: {
    "v-media": media,
    "v-card-info": cardInformativo,
  },
  data: () => ({
    texto: "Média de Módulos",
  }),
};
</script>

