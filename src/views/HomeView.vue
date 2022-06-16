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
          <td>{{ item.name }}</td>
          <td>{{ item.calories }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>


  export default {
    name: 'Home',
    data(){
      return{
        peliculas:[],
      }
    },
    mounted(){

    }
  }
</script>
