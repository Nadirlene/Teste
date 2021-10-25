<template>
  <v-card
    outlined
    class="mx-auto"
    max-height="180px"
    min-width="300"
    max-width="350"
    width="400"
    :height="altura"
  >
    <v-card-text class="mb-0">
      <v-row>
        <v-col cols="8"
          ><label>{{ descricao }}</label>
        </v-col>
        <v-col cols="4">
          <span class="float-right">{{ data }}</span>
        </v-col>
      </v-row>
      <v-row v-if="qtdAulas" style="justify-content: end; padding-right: 20px">
        <span>{{ qtdAulas }}</span>
      </v-row>
    </v-card-text>
    <v-card-text class="pt-0">
      <v-media
        :texto="texto"
        :valor="valor"
        :porcentagem="porcentagem"
        :tipoTexto="false"
      ></v-media>
    </v-card-text>
  </v-card>
</template>

<script>
import media from "@/components/media/index.vue";
export default {
  components: {
    "v-media": media,
  },

  props: {
    descricao: String,
    porcentagem: String,
    valor: Number,
    data: String,
    altura: String,
    qtdAulas: String,
  },

  data: () => ({
    texto: "Conclusão",
  }),
};
</script>

