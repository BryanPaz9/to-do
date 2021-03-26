<template>
  <v-app>
    <v-app-bar
      app
      color="red darken-4"
      dark
    >


    </v-app-bar>

    <v-main>
    </v-main>
    
  </v-app>
</template>

<script>
//import GetList from './components/GetList.vue';
import EmployeesTable from './components/EmployeesTable.vue'


export default {
  name: 'App',

  components: {
    //GetList,
    EmployeesTable
  },

  data: () => ({
    //
  }),
};
</script>
