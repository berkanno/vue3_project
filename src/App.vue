<template>
  <div>
    <v-card max-width="100%" class="mx-4 pa-0 mb-1 mt-1" color="grey-darken-4">
      <v-btn text class="mx-4 my-2" color="deep-purple-darken-4">
        <router-link to="/" class="txtdec">Home </router-link>
      </v-btn>
      <v-btn class="mx-4 my-2" color="deep-purple-darken-4">
        <router-link to="/about" class="txtdec"
          >About
        </router-link>
      </v-btn>
      <v-btn class="mx-4 my-2" color="deep-purple-darken-4">
        <router-link to="/search" class="txtdec"
          >Search
        </router-link>
      </v-btn>
      <v-btn class="mx-4 my-2" color="deep-purple-darken-4">
        <router-link to="/searchagigrid" class="txtdec"
          >Search Agi-grid
        </router-link>
      </v-btn>
    </v-card>

    <router-view />
  </div>
</template>

<script setup>
</script>
<style>
.txtdec{
  text-decoration: none;
  color:aqua;
}
</style>
