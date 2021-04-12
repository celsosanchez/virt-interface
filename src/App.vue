<template>
  <v-app id="inspire">
    <v-system-bar app>
      <v-icon @click="drawer = !drawer">{{
        drawer ? "mdi-arrow-expand-left" : "mdi-arrow-expand-right"
      }}</v-icon>
      <v-spacer></v-spacer>

      <v-icon @click="theme()">{{
        $vuetify.theme.dark ? "mdi-weather-sunny" : "mdi-sunglasses"
      }}</v-icon>

      <v-icon>mdi-triangle</v-icon>
    </v-system-bar>

    <v-navigation-drawer v-model="drawer" app true>
      <v-sheet color="dark lighten-4" class="pa-4">
        <v-avatar class="mb-4" color="grey darken-1" size="64"></v-avatar>

        <div>john@vuetifyjs.com</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>
        <v-list-item v-for="[icon, text, dir] in links" :key="icon" link>
          <v-list-item-icon>
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <!-- <router-link >{{dir}}</router-link> -->
            <v-list-item-title
              @click="$route.path !== `${dir}` ? $router.push(dir) : null"
              >{{ text }}</v-list-item-title
            >
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container class="py-8 px-6" fluid>
        <v-row>
          <router-view />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
// import axios from "axios";

export default {
  name: "App",

  components: {
    // HelloWorld,
  },

  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: false,
    links: [
      ["mdi-inbox-arrow-down", "Inbox", "/"],
      ["mdi-send", "Send", "/About"],
      ["mdi-delete", "Trash", "/NotFound"],
      ["mdi-alert-octagon", "Spam", "/"],
    ],
  }),
  methods: {
    theme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
      console.log(this.$vuetify);
      console.log(this.$route.path);
    },
   
  },
   
};
</script>
