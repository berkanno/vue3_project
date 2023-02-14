<template>
  <div>

  <v-card max-width="100%" class="mx-4 pa-0 mb-1 mt-1" color="grey-darken-4">

    <v-btn text class="mx-4 my-2" color="deep-purple-darken-4" >

  <router-link to="/" tag="li"><a style="color:aliceblue;">Home</a> </router-link>
    </v-btn>
    <v-btn class="mx-4 my-2" color="deep-purple-darken-4">

  <router-link to="/about" tag="li"><a style="color:aliceblue;">About</a> </router-link>
    </v-btn>
    <v-btn class="mx-4 my-2" color="deep-purple-darken-4">

<router-link to="/search" tag="li"><a style="color:aliceblue;">Search</a> </router-link>
  </v-btn>
  </v-card>
 

 

  <router-view />
 
  </div>

  


 
</template>

<script setup>
  //
</script>
