<template>
  <v-card outlined class="mx-auto" max-height="150px" min-width="300" max-width="400" height="110px" width="400">
    
    <v-card-text>
      <v-row >
        <v-col cols="8"><label class="text-wrap">{{ descricao }}</label></v-col>
        <v-col cols="4"> <span class="float-right">{{ data }}</span></v-col>
      </v-row>
      
     
    </v-card-text>
    <v-card-text class="pt-0" >
      <v-media width="50%"
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

