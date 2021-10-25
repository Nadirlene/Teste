<template>
  <v-card
    outlined
    class="mx-auto"
    max-height="100px"
    max-width="350"
    height="100px"
    width="330"
  >
      <v-card-text class="mb-0">
      <v-row >
        <v-col cols="8"><label >{{ texto }}</label></v-col>
        <v-col cols="4"> <v-icon :color="situacao ? 'light-green' : 'gray'">mdi-checkbox-marked-circle</v-icon></v-col>
      </v-row> 
     
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