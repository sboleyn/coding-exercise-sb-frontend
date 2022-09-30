<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <span class="mr-2">Coding Exercise</span>
    </v-app-bar>

    <v-main>
      <DataTable />
    </v-main>
  </v-app>
</template>

<script>
import DataTable from "./components/DataTable";

export default {
  name: "App",

  components: {
    // HelloWorld,
    DataTable,
  },

  data: () => ({
    //
  }),
};
</script>
