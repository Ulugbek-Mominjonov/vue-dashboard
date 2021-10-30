<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
      </div>
      <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
      <v-spacer></v-spacer>

      <template v-if="$vuetify.breakpoint.mdAndUp">
        <v-btn
          text
          rounded
          :key="`${link.label}-header-link`"
          v-for="link in links"
          :to="link.url"
        >
          <v-icon class="mr-1">mdi-{{link.icon}}</v-icon>
          <span class="mr-1">{{ link.label }}</span>
        </v-btn>
      </template>

      <template v-if="!$vuetify.breakpoint.mdAndUp">
        <v-menu
          left
          bottom
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              icon
              v-bind="attrs"
              v-on="on"
            >
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item
              v-for="link in links"
              :key="link.label"
              @click="() => {}"
            >
              <v-list-item-title>
                <v-btn
                  text
                  rounded
                  :to="link.url"
                >
                  <v-icon class="mr-1">mdi-{{link.icon}}</v-icon>
                  <span class="mr-1">{{ link.label }}</span>
                </v-btn>
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </template>
    </v-app-bar>
    <!-- MAIN  -->
    <v-main>
      <router-view />
    </v-main>

    <v-footer
      color="primary lighten-1"
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
        <v-btn
          v-for="link in links"
          :key="`${link.label}-footer-link`"
          color="white"
          text
          rounded
          class="my-2"
          :to="link.url"
        >
          {{ link.label }}
        </v-btn>
        <v-col
          class="primary lighten-2 py-4 text-center white--text"
          cols="12"
        >
          {{ new Date().getFullYear() }} — <strong>Vuetify Dashboard</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    links: [
      {
        label: 'Home',
        icon: 'home',
        url: '/'
      },
      {
        label: 'Login',
        icon: 'login',
        url: '/login'
      },
      {
        label: 'Dashboard',
        icon: 'view-dashboard',
        url: '/dashboard'
      },
      {
        label: 'Sign up',
        icon: 'account-plus',
        url: '/signup'
      }
    ]
  }),
};
</script>
