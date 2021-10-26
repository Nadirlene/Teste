<template>
  <v-card outlined>
    <v-card-text>
      <v-row>
        <v-col cols="10">
          <strong>{{ texto }}</strong>
        </v-col>
        <v-col cols="2">
          <v-icon :color="situacao ? 'light-green' : 'gray'">
            mdi-checkbox-marked-circle
          </v-icon>
        </v-col>
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