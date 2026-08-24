<template>
  <v-app>
    <v-app-bar>
      <template v-slot:prepend>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
      </template>

      <v-app-bar-title>庇護工場快速查詢</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <!-- <HelloWorld /> -->
      <filterList />
    </v-main>
    <!-- <v-btn
      class="ma-2"
      icon="mdi-theme-light-dark"
      location="top right"
      position="absolute"
      @click="$vuetify.theme.cycle()"
    /> -->
  </v-app>
</template>

<script lang="ts" setup>
// import HelloWorld from '@/components/HelloWorld.vue'
import filterList from './components/filterList.vue';
</script>
