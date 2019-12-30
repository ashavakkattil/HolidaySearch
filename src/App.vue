<template>
  <v-app>
    
      <AppHeader />
    

    <v-content>
      <Home />
    </v-content>
    <AppFooter/>
  </v-app>
</template>

<script>
import Home from "./components/Home";
import AppHeader from "./components/AppHeader";
import AppFooter from "./components/AppFooter";

export default {
  name: "App",

  components: {
    Home,
    AppHeader,
    AppFooter
  },

  data: () => ({
    //
  })
};
</script>
