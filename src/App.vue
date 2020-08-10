<template>
  <v-app id="inspire">
    <v-app id="inspire">
      <v-navigation-drawer
        v-model="drawer"
        app
      >
      <Menu></Menu>
      </v-navigation-drawer>
      <v-app-bar
        app
        color="primary"
        dark
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>ZOOM</v-toolbar-title>
      </v-app-bar>
      <v-main>
        <v-container
          class="fill-height"
          fluid
        >
          <v-row
            align="center"
            justify="center"
          >
            <v-col class="text-center">
              <v-main>
                <hello-world></hello-world>
              </v-main>
            </v-col>
          </v-row>
        </v-container>      
      </v-main>
      <v-footer
        color="primary"
        app
      >
        <span class="white--text">&copy; 2020</span>
      </v-footer>
    </v-app>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import Menu from './components/menu/Menu.vue';

export default Vue.extend({
  name: 'App',

  components: {
    HelloWorld,
    Menu,
  },

  data: () => ({
    drawer: false,
    offset: true,
    show: false,
  }),
});
</script>
