<template>
  <v-app id="employeesTable">
    <v-card>
      <v-card-title>
        Listado de empleados
        <v-spacer></v-spacer>
        <v-text-field
          v-model="search"
          append-icon="mdi-magnify"
          label="Search"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      <v-data-table
        :headers="headers"
        :items="employees"
        :search="search"
      ></v-data-table>
    </v-card>
  </v-app>
</template>

<script>
import axios from "axios"
export default {
    name: 'EmployeesTable',
    data: ()=>({
      search: '',
      headers: [
        {
          text: 'Código de trabajador',
          align: 'start',
          sortable: false,
          value: 'code',
        },
        { text: 'Nombre', value: 'firstName' },
        { text: 'Apellido', value: 'lastName' },
        { text: 'Email', value: 'email' },
        { text: 'Edad', value: 'age' },
        { text: 'ID', value: '_id' },
      ],
      employees: [],
    }),
    mounted() {
     //axios({method:"GET", "url":"http://200.49.170.195:3030/viaje/listaclientexls"}).then(response =>(this.employees = response.data))  
     axios({method:"GET", "url":"http://localhost:3000/api/v1/employees"}).then(response =>(
         this.employees = response.data.employees));  
    },
}
</script>