<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" persistent max-width="600px">
      <template v-slot:activator="{ on, attrs }">
        <v-btn color="primary" dark v-bind="attrs" v-on="on"> Añadir Pelicula</v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">Añadir Pelicula</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Nombre*" v-model="datos.nombre" text required></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Sinopsis*" v-model="datos.sinopsis" text required></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Estrellas*" v-model="datos.estrellas" required></v-text-field>
              </v-col>
            </v-row>
          </v-container>
          <small>* indica que el campo es requerido</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="dialog = false"> Cerrar </v-btn>
          <v-btn color="blue darken-1" text @click="enviar(),dialog = false"> Guardar </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
  export default {
    data: () => ({
      dialog: false,
      'datos':{'nombre':null,'sinopsis':null,'estrellas':null}

    }),
    methods:{
        enviar(){
            this.datos.estrellas = Number(this.datos.estrellas);
            this.axios.post('http://127.0.0.1:8000/api/peliculas',this.datos)
            .then(
                console.log('El elemento ha sido añadido')
            )
            .catch(error =>{
                console.log(error);
            })
        }
    }
  }
</script>