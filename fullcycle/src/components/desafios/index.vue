<template>
  <v-card
    outlined
    class="mx-auto"
    max-height="100px"
    max-width="400"
    height="100px"
    width="400"
  >
    <v-card-text>
      <label class="text-h8 text--primary">{{ texto }}</label>
      <v-chip class="ma-2" color="light-green">
        <v-avatar left>
          <v-icon>mdi-checkbox-marked-circle</v-icon>
        </v-avatar></v-chip
      >
    </v-card-text>
  </v-card>
</template>


<script>
export default {
  props: {
    texto: String,
    situacao: Boolean,
  },
};
</script>