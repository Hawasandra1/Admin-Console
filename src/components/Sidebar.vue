<template>
  <v-navigation-drawer v-model="drawer" app>
    <v-img height="140" class="pa-4" src="">
      <div class="text-center">
        <v-avatar class="mb-4" color="grey darken-1" size="64">
          <v-img aspect-ratio="30" src="@/assets/logo.png" />
        </v-avatar>
        <h2 class="white--text">Admin Console</h2>
      </div>
    </v-img>
    <v-divider></v-divider>
    <v-list>
      <v-list-item v-for="[icon, text] in links" :key="icon" link>
        <v-list-item-icon>
          <v-icon>{{ icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ text }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: "Sidebar",
  props: ["drawer"],
  data() {
    return {
      links: [
        ["mdi-view-dashboard", "Dashboard"],
        ["mdi-briefcase", "Projects"],
        ["mdi-check-circle", "Tasks"],
        ["mdi-account-multiple", "Teams"],
        ["mdi-chart-line", "Reports"],
        ["mdi-settings", "Settings"],
      ],
    };
  },
};
</script>

<style scoped></style>
