<template>
  <div id="app">
    <v-app>
      <!-- v-if="$store.state.isLoggedIn" -->
      <HeaderComp  />
      <v-main>
        <router-view />
      </v-main>
      <!-- v-if="$store.state.isLoggedIn" -->
      <FooterComp />
    </v-app>
  </div>
</template>

<script>
import HeaderComp from './components/Navigation/HeaderComp.vue';
import FooterComp from './components/Navigation/FooterComp.vue';

export default {
  name: 'App',

  components: {
    HeaderComp,
    FooterComp
  },

  data: () => ({
    // state:false,
  }),
};
</script>



<style scoped>
@import url("assets/Style/style.css");
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@200&display=swap');
/* .MyMenuBtn:hover {
  background-color: transparent !important;
  border: 1px solid red !important;
} */
</style>
