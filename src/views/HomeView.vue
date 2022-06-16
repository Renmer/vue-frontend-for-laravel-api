<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">
            Nombre
          </th>
          <th class="text-center">
            Sinopsis
          </th>
          <th class="text-center">
            Estrellas
          </th>
          <th class="text-center">
            Opciones
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in peliculas"
          :key="item.name"
        >
          <td>{{ item.nombre }}</td>
          <td>{{ item.sinopsis }}</td>
          <td>{{ item.estrellas }} <v-icon small></v-icon></td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
//import { mdiStarCheckOutline } from '@mdi/js';
  export default {
    name: 'Home',
    data(){
      return{
        peliculas:[],
      }
    },
    /*components:{
      mdiStarCheckOutline
    },*/
    mounted(){
      this.axios.get('http://127.0.0.1:8000/api/peliculas')
      .then(response => (this.peliculas = response.data))
    }
  }
</script>
