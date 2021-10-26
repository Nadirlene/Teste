<template>
  <v-app>
    <v-app-bar app color="grey darken-4">
      <v-responsive max-width="300">
        <v-text-field
          dark
          class="ml-10 mt-5"
          color="#ffca28"
          label="Buscar"
          append-icon="mdi-magnify"
        ></v-text-field>
      </v-responsive>
    </v-app-bar>
    <v-navigation-drawer app fixed>
      <v-app-bar color="grey darken-4">
        <v-img
          class="ml-5"
          src="@/assets/logoFullCycle.jpeg"
          height="45%"
          width="45%"
        >
        </v-img>
        <v-app-bar-nav-icon
          color="white"
          class="icone-menu"
          heigth="50px"
          width="51px"
        ></v-app-bar-nav-icon>
      </v-app-bar>

      <v-list class="mt-5">
        <v-list-item class="px-2">
          <v-list-item-avatar class="mx-auto">
            <v-img
              src="https://randomuser.me/api/portraits/women/85.jpg"
            ></v-img>
          </v-list-item-avatar>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6 mb-0">
              <p class="text-center mb-0">Nadirlene</p>
            </v-list-item-title>
            <v-list-item-subtitle>
              <p class="text-center yellow--text">Administrador</p>
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-list>
        <v-list-item-group>
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account-multiple</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Turmas</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-icon>
              <v-icon color="#ffca28">mdi-school</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Estudantes</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>

      <v-divider></v-divider>
    </v-navigation-drawer>

    <v-main>
      <v-container class="container">
        <v-row class="pb-5">
          <v-info-usuario
            :nome="objetoEstudante.nome"
            :email="objetoEstudante.email"
            :primeiroAcesso="objetoEstudante.primeiroAcesso"
            :ultimoAcesso="objetoEstudante.ultimoAcesso"
            :porcentagem="objetoEstudante.mediaGeralPorcentagem"
            :valor="objetoEstudante.mediaGeral"
          >
          </v-info-usuario>
        </v-row>

        <v-row>
          <v-divider></v-divider>
        </v-row>

        <v-row>
          <v-col cols="12" sm="12" md="8">
            <v-card elevation="0">
              <v-card-title>Cursos</v-card-title>
              <v-card-text>
                <v-col cols="12" md="4" sm="12" class="mt-5 pr-4">
                  <v-card-info
                    style="border-color: #ffca28"
                    :descricao="objetoCursos.descricaoCurso"
                    :porcentagem="objetoCursos.mediaCursoPorcentagem"
                    :valor="objetoCursos.mediaCurso"
                    :data="objetoCursos.data"
                  />
                </v-col>
              </v-card-text>
            </v-card>
          </v-col>

          <v-spacer></v-spacer>
          <v-col cols="12" md="3" sm="12" class="mt-5 pr-4">
            <v-media
              :texto="'Média Geral'"
              :valor="objetoCursos.mediaCursoGeral"
              :porcentagem="objetoCursos.mediaCursoGeralPorcentagem"
              :tipoTexto="tipoTextoMedia"
            ></v-media>
          </v-col>
        </v-row>

        <v-row>
          <v-col>
            <v-card color="grey lighten-5">
              <v-row>
                <v-col cols="12" md="2" sm="12">
                  <v-card color="grey lighten-5" elevation="0">
                    <v-card-title>Módulos</v-card-title>
                  </v-card>
                </v-col>

                <v-col cols="12" md="4" sm="12">
                  <v-card color="grey lighten-5" elevation="0">
                    <v-card-text>{{ objetoCursos.descricaoCurso }}</v-card-text>
                  </v-card>
                </v-col>

                <v-spacer></v-spacer>
                <v-col cols="12" md="3" sm="12" class="mt-5 pr-4">
                  <v-media
                    :texto="'Média de Modulos'"
                    :valor="objetoCursos.mediaCursoGeral"
                    :porcentagem="objetoCursos.mediaCursoGeralPorcentagem"
                    :tipoTexto="tipoTextoMedia"
                  ></v-media>
                </v-col>
              </v-row>
              <div style="padding: 1%">
                <v-squad :objetoFor="objetoModulos" />
              </div>
            </v-card>
          </v-col>
        </v-row>

        <v-row style="padding: 1%">
          <v-divider></v-divider>
        </v-row>

        <v-row>
          <v-col cols="12" md="8" sm="12">
            <v-card color="grey lighten-5">
              <v-row>
                <v-col cols="12" md="3" sm="12">
                  <v-card color="grey lighten-5" elevation="0" cols="12" md="8">
                    <v-card-title>Capítulos</v-card-title>
                  </v-card>
                </v-col>
                <v-col cols="12" md="5" sm="12">
                  <v-card color="grey lighten-5" elevation="0">
                    <v-card-text>{{ objetoModulos[0].descricao }}</v-card-text>
                  </v-card>
                </v-col>
                <v-col cols="12" md="4" sm="12" class="mt-5 pr-4">
                  <v-media
                    :texto="'Média de Capitulos'"
                    :valor="objetoCursos.mediaCursoGeral"
                    :porcentagem="objetoCursos.mediaCursoGeralPorcentagem"
                    :tipoTexto="tipoTextoMedia"
                  ></v-media>
                </v-col>
              </v-row>
              <div style="padding: 1%">
                <v-squad :md="'6'" :objetoFor="objetoCapitulos" />
              </div>
            </v-card>
          </v-col>

          <v-col cols="12" md="4" class="pt-0">
            <v-card color="grey lighten-5">
              <v-card-title class="pt-7 pb-6"> Desafios </v-card-title>
              <v-row
                class="desafio-card"
                v-for="(item, index) in objetoDesafios"
                :key="index"
              >
                <v-col cols="12">
                  <v-desafios
                    :texto="item.descricao"
                    :situacao="item.situacao"
                  ></v-desafios>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import squad from "@/components/squad/index.vue";
import infoUsuario from "@/components/info_usuario/index.vue";
import desafios from "@/components/desafios/index.vue";
import { estudante } from "@/objetos/objeto.js";
import cardInformativo from "@/components/card_informativo/index.vue";
import media from "@/components/media/index.vue";

export default {
  components: {
    "v-squad": squad,
    "v-info-usuario": infoUsuario,
    "v-desafios": desafios,
    "v-card-info": cardInformativo,
    "v-media": media,
  },

  data: () => ({
    objetoEstudante: estudante,
    objetoModulos: estudante.cursos[0].modulos,
    objetoCursos: estudante.cursos[0],
    objetoCapitulos: estudante.cursos[0].modulos[0].capitulos,
    objetoDesafios: estudante.desafios,
    tipoTextoMedia: true,
  }),
};
</script>

<style scoped>
.container {
  padding: 3%;
}
.v-list-item-group .v-list-item--active {
  background: #ffca28;
}
.v-list--nav {
  padding-left: 0px;
  padding-right: 0px;
  border-left: 20px;
}
.v-list--nav .v-list-item,
.v-list--nav .v-list-item:before {
  min-height: 60px;
  border-radius: 0px;
  padding: 0 48px;
}
.desafio-card {
  padding: 2%;
}
</style>