<template>
  <v-card min-height="140px" outlined>
    <v-card-text>
      <v-row>
        <v-col cols="8">
          <strong>{{ descricao }}</strong>
        </v-col>
        <v-col cols="4">
          <span class="float-right">{{ data }}</span>
        </v-col>
      </v-row>
      <v-row v-if="qtdAulas" class="pr-3">
        <v-spacer></v-spacer>
        {{ qtdAulas }}
      </v-row>
    </v-card-text>
    <v-card-actions class="pl-5">
      <v-media
        :size-text="'12'"
        :texto="texto"
        :valor="valor"
        :porcentagem="porcentagem"
        :tipoTexto="false"
      />
    </v-card-actions>
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
    qtdAulas: String,
  },

  data: () => ({
    texto: "Conclusão",
  }),
};
</script>

