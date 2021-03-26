<template>
  <v-app id="getlist">
    <v-card>
      <v-card-title>
        Listado de clientes
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
        :items="desserts"
        :search="search"
      ></v-data-table>
    </v-card>
  </v-app>
</template>

<script>
import axios from "axios"
export default {
    name: 'GetList',
    data: ()=>({
      search: '',
      headers: [
        {
          text: 'Placa',
          align: 'start',
          sortable: false,
          value: 'Placa',
        },
        { text: 'Furgon', value: 'Furgon' },
        { text: 'Origen', value: 'Origen' },
        { text: 'Destino', value: 'Destino' },
        { text: 'Transportista', value: 'Transportista' },
        { text: 'Piloto', value: 'Piloto' },
      ],
      desserts: [],
    }),
    mounted() {
      axios({method:"GET", "url":"http://200.49.170.195:3030/viaje/listaclientexls"}).then(response =>(this.desserts = response.data))  
    },
}
</script>