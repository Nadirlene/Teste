<template>
  <v-row>
    <v-col
      cols="12"
      :md="md ? md : '4'"
      sm="12"
      v-for="(item, index) in objetoFor"
      :key="index"
    >
      <v-card-info
        :descricao="item.descricao"
        :porcentagem="item.porcentagem"
        :valor="item.valor"
        :data="item.data"
        :qtdAulas="item.qtdAulas"
      />
    </v-col>
  </v-row>
</template>

<script>
import cardInformativo from "@/components/card_informativo/index.vue";
export default {
  props: {
    md: String,
    objetoFor: Array,
  },
  components: {
    "v-card-info": cardInformativo,
  },
};
</script>

