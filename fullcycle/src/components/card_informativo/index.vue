<template>
  <v-card outlined class="mx-auto" max-height="100px" max-width="400" height="100px" width="400">
    <v-card-text>
      <label class="text-h8 text--primary">{{ descricao }}</label>
      <span>{{ data }}</span>
    </v-card-text>
    <v-card-text>
      <v-media
        :texto="texto"
        :valor="valor"
        :porcentagem="porcentagem"
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
    // qtdAulas: String,
  },

  data: () => ({
    texto: "Conclusão",
  }),
};
</script>

