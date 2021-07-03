<template>
  <v-app>
    <v-app-bar
      app
      color="#B98FE4"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Lambda Logo"
          class="shrink mr-2"
          contain
          src=""
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Lambda"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src=""
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="/"
        text
      >
        <span class="mr-2"> More </span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>

    <v-footer color="#B98FE4" dark>
      <v-row justify="center" no-gutters>
        <v-col
        class="#B98FE4 py-4 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — tatatakky
      </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'App',

  data: () => ({
    //
  }),
});
</script>

<style scoped>
v-card__text .footer-text {
  text-align: center;
}
</style>
