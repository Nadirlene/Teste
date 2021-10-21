<template>
  <!-- <v-container fluid> -->
  <v-app>
    <!-- NAV BAR -->
    <v-toolbar color="grey darken-4">
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
      <v-app-bar-nav-icon color="white" class="icone-menu"></v-app-bar-nav-icon>

      <v-divider class="barra" vertical></v-divider>

      <v-spacer></v-spacer>
      <v-divider vertical ligth></v-divider>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
    <!-- FIM NAV BAR -->
    
      <!-- MENU LATERAL -->
    <v-navigation-drawer  class="menu-side" >
      <v-list class="mt-5">
        <v-list-item class="px-2">
          <v-list-item-avatar class="mx-auto">
            <v-img
              src="https://randomuser.me/api/portraits/women/85.jpg"
            ></v-img>
          </v-list-item-avatar>
        </v-list-item>

        <v-list-item link>
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

      <v-list class="lista" nav dense>
        <v-list-item-group>
          <v-list-item>
            <v-list-item-icon>
              <v-icon pr-3>mdi-account-multiple</v-icon>
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
    <!-- FIM MENU LATERAL -->
    <!-- </v-card>
   </div> -->
  </v-app>
  <!-- </v-container> -->
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    drawer: true,
    group: null,
  }),
};
</script>

<style scoped>

.theme--light.v-divider.barra {
  border-color: #424141 !important;
}


.v-list--nav {
  padding: 10px;
  padding-left: 0px;
  padding-right: 0px;
}

.v-list--nav .v-list-item,
.v-list--nav .v-list-item:before {
  min-height: 60px;
  border-radius: 0px;
}
.v-list-item-group .v-list-item--active {
  background: #ffca28;
}
</style>
