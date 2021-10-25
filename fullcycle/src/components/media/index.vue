<template>
  <v-row class="mb-5">
    <v-col cols="12">
      <p v-if="tipoTexto" class="subtitle-2 font-weight-bold pt-2 mb-0">{{texto}}</p>
      <p v-if="!tipoTexto" class="teste">{{texto}}</p>
      <v-row class="teste">
        <v-col  cols="10">
          <v-progress-linear class="mt-2 bottom" color="#ffca28" height="7" rounded :value="valor"></v-progress-linear>
        </v-col>
        <v-col cols="2">
          <label class="subtitle-2">{{ porcentagem }}</label>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: {
    texto:String,
    porcentagem: String,
    valor: Number,
    tipoTexto:Boolean
  },
};
</script>

<style scoped>
.teste{
  font-size: 10px;
  padding: 0%;
  margin-bottom: 0px;
}
/* p {
line-height: 10px;
} */
</style>
