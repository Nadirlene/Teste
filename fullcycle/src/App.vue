<template>
  <v-app>
    <!-- app bar -->
    <v-app-bar app color="grey darken-4">
      <v-toolbar-side-icon>
        <v-img
          display="block"
          class="ml-5"
          src="@/assets/logoFullCycle.jpeg"
          height="45%"
          width="45%"
        >
        </v-img>
      </v-toolbar-side-icon>
      <v-app-bar-nav-icon
        color="white"
        class="icone-menu"
        heigth="50px"
        width="51px"
      ></v-app-bar-nav-icon>
      <v-divider vertical class="barra pr-4"></v-divider>
      <v-responsive max-width="300">
        <v-text-field
          dense
          class="ml-10 mt-5"
          color="yellow"
          label="Buscar"
          append-icon="mdi-magnify"
        ></v-text-field>
      </v-responsive>
    </v-app-bar>
    <!-- fim app bar -->

    <!-- navigation drawer -->
    <v-navigation-drawer class="mt-15" width="320">
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

      <v-list class="lista" nav>
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
    <!-- fim navigation drawer -->

    <v-main>
      <!--  -->
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: null,
    links: [
      ["mdi-inbox-arrow-down", "Inbox"],
      ["mdi-send", "Send"],
      ["mdi-delete", "Trash"],
      ["mdi-alert-octagon", "Spam"],
    ],
  }),
};
</script>

<style scoped>
.theme--light.v-divider.barra {
  border-color: #424141 !important;
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
</style>
