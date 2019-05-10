<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>User Notes App</span>
        <span class="font-weight-light">AWS TEST</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>

    <v-content>
      <getnotes/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import getnotes from "./components/getnotes";
export default {
  name: "App",
  components: {
    HelloWorld,
    getnotes
  },
  data() {
    return {
      //
    };
  }
};
</script>
