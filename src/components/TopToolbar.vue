<template>
  <div>
    <v-navigation-drawer app fixed v-model="showMenu">
      <v-list dense>
        <v-list-item @click="doNothing">
          <v-list-item-action>
            <v-icon>settings</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item :to="{ path: '/about'}">
          <v-list-item-action>
            <v-icon>help</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Help</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app fixed dark color="primary">
      <v-app-bar-nav-icon @click.stop="toggleMenu"></v-app-bar-nav-icon>

      <v-toolbar-title>Metro Yaab!</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon @click="darkMode">
        <v-icon>mdi-theme-light-dark</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-information</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
@Component
export default class TopToolbar extends Vue {
  showMenu = false;
  toggleMenu(): void {
    this.showMenu = !this.showMenu;
  }
  doNothing(): void {
    // do nothing.
  }
  darkMode(): void {
    this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    localStorage.setItem('isDark', this.$vuetify.theme.dark + "")
  }
}
</script>