<template>
  <v-row>
    <v-col cols="12">
      <h6>{{texto}}</h6>
      <v-row>
        <v-col cols="8">
          <v-progress-linear color="red" rounded :value="valor"></v-progress-linear>
        </v-col>
        <v-col cols="4">
          <label>{{ porcentagem }}</label>
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
  },
};
</script>

