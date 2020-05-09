<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center headline">
        LYBRARIE BOOKSHOP
      </div>

      <v-spacer></v-spacer>

      <v-btn class="mx-4">
        <v-icon left>mdi-plus</v-icon>

        Add Book
      </v-btn>

      <v-btn>
        <v-icon left>mdi-file</v-icon>
        View Reports
      </v-btn>

    </v-app-bar>

    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
