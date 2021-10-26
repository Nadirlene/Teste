<template>
  <v-row>
    <v-col>
      <strong v-if="tipoTexto">
        {{ texto }}
      </strong>
      <strong
        v-if="!tipoTexto"
        :style="sizeText ? `font-size:${sizeText}px` : 'font-size:15px'"
        >{{ texto }}
      </strong>
      <v-row>
        <v-col cols="12" md="6" sm="12">
          <v-progress-linear
            class="mt-2 bottom"
            color="#ffca28"
            height="7"
            rounded
            :value="valor"
          ></v-progress-linear>
        </v-col>
        <v-col cols="12" md="4" sm="12">
          <label class="subtitle-2">{{ porcentagem }}</label>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: {
    texto: String,
    porcentagem: String,
    valor: Number,
    tipoTexto: Boolean,
    sizeText: String,
  },
};
</script>
