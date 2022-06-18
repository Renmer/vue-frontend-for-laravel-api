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
        <tr v-for="item in peliculas" :key="item.id">
          <td class="text-left">{{ item.nombre }}</td>
          <td class="text-center">{{ item.sinopsis }}</td>
          <td class="text-center">{{ item.estrellas }}<star-icon /></td>
          <td class="text-center">
            <v-btn><pencil-icon/></v-btn>
            <v-spacer/>
            <v-btn color="error" @click="eliminar(item.id)"><delete-icon/></v-btn>
          </td>
        </tr>
      </tbody>
      <creacion-component/>
    </template>
  </v-simple-table>
</template>


<script>
import StarIcon from 'vue-material-design-icons/Star.vue';
import DeleteIcon from 'vue-material-design-icons/Delete.vue';
import PencilIcon from 'vue-material-design-icons/Pencil.vue';
import CreacionComponent from '@/components/CreacionComponent.vue'
  export default {
    name: 'Home',
    data(){
      return{
        peliculas:[],
      }
    },
    components: {
      StarIcon,
      DeleteIcon,
      PencilIcon,
      CreacionComponent
    },
    created(){
      this.axios.get('http://127.0.0.1:8000/api/peliculas')
       .then(response => (this.peliculas = response.data))
    },
    methods:{
      eliminar(id){
        this.axios.delete('http://127.0.0.1:8000/api/peliculas/'+id)
         .then(
            console.log('Pelicula con id: '+id+ ' ha sido eliminado')
          )
         .catch(error =>{
          console.log(error);
         })
      },
    }
  }
</script>
