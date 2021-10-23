<template>
	<v-app light>
		<singleton-snackbar />
		<v-navigation-drawer
			v-model="drawer"
			fixed
			app
			color="white"
		>
			<v-list-item two-line class="primary">
				        <v-img
          display="block"
          class="ml-5"
          src="@/assets/logoFullCycle.jpeg"
          height="45%"
          width="45%"
        >
        </v-img>
			</v-list-item>
			<span v-for="item in items" :key="item.title">
				<span v-if="isParceidoAllowed(item.allow)"> </span>
				<v-list-group
					v-if="item.subroutes"
					v-model="item.active"
					:prepend-icon="item.icon"
					no-action
				>
					<template v-slot:activator>
						<v-list-item-content>
							<v-list-item-title v-text="item.title"></v-list-item-title>
						</v-list-item-content>
					</template>

					<v-list-item
						v-for="subroute in item.subroutes"
						:key="subroute.title"
						:to="subroute.to"
					>
						<v-list-item-content>
							<v-list-item-title v-text="subroute.title"></v-list-item-title>
						</v-list-item-content>
					</v-list-item>
				</v-list-group>
				<v-list-item v-else :to="item.to">
					<v-list-item-action>
						<v-icon>{{ item.icon }}</v-icon>
					</v-list-item-action>
					<v-list-item-content>
						<v-list-item-title v-text="item.title" />
					</v-list-item-content>
				</v-list-item>
			</span>
		</v-navigation-drawer>

		<v-app-bar fixed app light color="primary" elevation="0" class="app-bar">
			<v-app-bar-nav-icon class @click.stop="drawer = !drawer" />
			<v-spacer />

			<!-- MENU DIREITO -->

			<v-menu v-model="menu" offset-y>
				<template v-slot:activator="{ on }">
					<v-btn icon v-on="on">
						<v-avatar
							v-if="!user.nomeArquivo.includes('empty')"
							color="primary"
						>
							<v-img
								:src="user.site + user.controller + '/' + user.nomeArquivo"
							></v-img>
						</v-avatar>
						<v-avatar v-else color="primary" class="darken-2">
							<span class="white--text">{{ user.nome | getInitials }}</span>
						</v-avatar>
					</v-btn>
				</template>

				<v-card width="300px">
					<v-list>
						<!-- RESUMO DO PERFIL -->
						<v-list-item>
							<v-list-item-content>
								<v-list-item-title>{{ user.nome }}</v-list-item-title>
								<v-list-item-subtitle>{{
									user.empresa.nome
								}}</v-list-item-subtitle>
							</v-list-item-content>
						</v-list-item>

						<v-divider></v-divider>

						<!-- LISTA DE OPÇÕES -->
						<v-list-item nuxt link to="/usuarios/perfil">
							<v-list-item-title>Perfil</v-list-item-title>
						</v-list-item>
						<v-list-item @click="logoutUser">
							<v-list-item-title>Logout</v-list-item-title>
						</v-list-item>
					</v-list>
				</v-card>
			</v-menu>
		</v-app-bar>

		<!-- CONTEÚDO DO SITE -->
		<v-main>
			<v-container fluid>
				<nuxt />
			</v-container>
		</v-main>
	</v-app>
</template>

<script>
import SingletonSnackbar from "@/components/snackbar/snackbar";
export default {
	auth: true,
	components: {
		"singleton-snackbar": SingletonSnackbar
	},
	data() {
		return {
			menu: false,
			drawer: true,
			fixed: true,
			items: [
				{
					icon: "mdi-apps",
					title: "Dashboard",
					to: "/dashboard",
					subroutes: false
				},
				{
					icon: "mdi-book",
					title: "Concursos",
					to: "/concursos",
					subroutes: false
				},
				{
					icon: "mdi-gavel",
					title: "Recursos",
					to: "/recursos",
					subroutes: [
						{
							title: "Configurações",
							to: "/recursos/configuracoes"
						},
						{
							title: "Solicitações",
							to: "/recursos/solicitacoes"
						}
					]
				},
				{
					icon: "mdi-account-tie",
					title: "Candidatos",
					to: "/candidatos",
					subroutes: false
				},
				{
					icon: "mdi-pencil",
					title: "Cadastro",
					subroutes: [
						{
							title: "Usuários",
							to: "/cadastro/usuarios"
						},
						{
							title: "Empresas",
							to: "/cadastro/empresas"
						},
						{
							title: "Anexos",
							to: "/cadastro/anexos"
						}
					]
				},
				{
					icon: "mdi-cog",
					title: "Configuração",
					allow: ["FUNCIONARIO", "ADMINISTRADOR"],
					subroutes: [
						{
							title: "Notícias",
							to: "/configuracoes/noticias"
						},
						{
							title: "Slideshows",
							to: "/configuracoes/slides"
						}
					]
				},
				{
					icon: "mdi-file-document",
					title: "Relatórios",
					to: "/relatorios",
					subroutes: false
				},
			],
			right: true
		};
	},
	methods: {
		logoutUser() {
			this.$auth.logout();
		},
		isParceidoAllowed(roles) {
			if (!roles) return;
			return roles.includes(TipoPerfil[this.user.role]);
		}
	},
	computed: {
		user() {
			return this.$store.state.auth.user;
		}
	},
	filters: {
		getInitials(name) {
			if (!name) return;
			return name
				.split(" ")
				.map(n => n[0])
				.join("")
				.substring(0, 2);
		}
	}
};
</script>
<style scoped>
.app-bar {
	border-bottom: 1px solid lightgray !important;
}
</style>
