<template>
  <v-app id="inspire">
    <v-app-bar app color="grey darken-4">
      <v-divider vertical class="barra pr-4"></v-divider>
      <v-responsive max-width="300">
        <v-text-field
          dark
          class="ml-10 mt-5"
          color="yellow"
          label="Buscar"
          append-icon="mdi-magnify"
        ></v-text-field>
      </v-responsive>
    </v-app-bar>
    <v-navigation-drawer app>
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
      <v-list class="lista">
        <v-list-item-group>
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account-multiple</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Turmas</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-school</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Estudantes</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
      <v-divider></v-divider>
    </v-navigation-drawer>

    <v-info-usuario class="mt-15" 
      :nome="objetoEstudante.nome"
      :email="objetoEstudante.email"
      :primeiroAcesso="objetoEstudante.primeiroAcesso"
      :ultimoAcesso="objetoEstudante.ultimoAcesso"
      :porcentagem="objetoEstudante.mediaGeralPorcentagem"
      :valor="objetoEstudante.mediaGeral"
    >
    </v-info-usuario>

    <v-divider></v-divider>
    <h2>Cursos</h2>
    <v-card-info
      :descricao="objetoCursos.descricaoCurso"
      :porcentagem="objetoCursos.mediaCursoPorcentagem"
      :valor="objetoCursos.mediaCurso"
      :data="objetoCursos.data"
    ></v-card-info>

    <v-media
      :texto="'Média Geral'"
      :valor="objetoCursos.mediaCursoGeral"
      :porcentagem="objetoCursos.mediaCursoGeralPorcentagem"
    ></v-media>
    <v-card>
      <v-squad
        :titulo="'Módulos'"
        :subtitle="objetoCursos.descricaoCurso"
        :porcentagem="objetoCursos.mediaModuloGeralPorcentagem"
        :valor="objetoCursos.mediaModuloGeral"
        :objetoFor="objetoModulos"
      ></v-squad>
    </v-card>


    <v-container class="content">
      <v-row>
        <v-col cols="6">
          <v-card>
            <v-squad
              :titulo="'Capítulos'"
              :subtitle="objetoCursos.modulos[0].descricao"
              :porcentagem="objetoCursos.mediaCapitulosGeralPorcentagem"
              :valor="objetoCursos.mediaCapitulosGeral"
              :objetoFor="objetoCapitulos"
            ></v-squad>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title> Desafios </v-card-title>
            <div v-for="(item, index) in objetoDesafios" :key="index">
              <v-desafios
                :texto="item.descricao"
                :situacao="item.situacao"
              ></v-desafios>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<style scoped>
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
.flip-card {
  display: flex;
  margin-bottom: 5rem;
}
.content {
  display: flex;
  flex-wrap: wrap;
  padding: 30px 0px 30px 300px;
  border: none;
}


</style>

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
  }),
};
</script>