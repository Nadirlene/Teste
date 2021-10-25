<template>
  <v-container class="content grey lighten-5">
    <v-row>
      <v-col cols="12">
        <v-row>
          <v-col cols="8">
            <v-row>
                 <h2>{{ titulo }}</h2>
            <label>{{ subtitle }}</label>
            </v-row>
         
          </v-col>
          <v-col cols="4">
            <v-media
              :texto="texto"
              :valor="valor"
              :porcentagem="porcentagem"
            ></v-media>
          </v-col>
          <!-- <v-col>

          </v-col> -->
        </v-row>
      </v-col>
    </v-row>

    <v-card-info
      class="mt-10"
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
</style>

