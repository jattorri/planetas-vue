<template>
  <div class="d-flex card mx-auto my-lg-3">
      <div class="row justify-content-center h-100">
      <span class="col-lg-6">
        <img class="img-responsive img-thumbnail my-lg-2" v-bind:src="imagen" />
        <div class="py-lg-1">
          <p><b>{{signo }}</b></p>
        </div>
      </span>
      <span class="col-lg-3 border-left">
        <div>
          <p>Elemento: <b>{{elemento}}</b></p>
          <p>Meses:
            <ul v-for="mes in meses" :key="mes">
                <li>
                  <b><p>{{m[mes]}}</p></b>
                </li>
            </ul>
          </p>
        <div class="d-flex h-25">
          <p>Descripcion: <b>{{descripcion}}</b></p>
        </div>
        </div>
      </span>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

    export default{
        name: 'DetalleCompleto',
        props: {
        },
          created(){
            this.getZodiaco(this.$route.params.id)
        },data(){
          return {
            id: 0,
            signo: '',
            elemento: '',
            imagen: '',
            meses: [],
            descripcion: '',
            m: [
              'Enero',
              'Febrero',
              'Marzo',
              'Abril',
              'Mayo',
              'Junio',
              'Julio',
              'Agosto',
              'Septiembre',
              'Octubre',
              'Noviembre',
              'Diciembre'
            ]
          }
        },
        methods:{
          async getZodiaco(numero){
            console.log(numero)
            try{       
                let data = await axios.get('http://localhost:8080/test/tb/zodiaco.json')
                let zodiacos = data.data;
                console.log(this.$route.query)
                zodiacos.map( z => {
                  if(z.id == numero){
                    this.id = numero;
                    this.signo = z.signo;
                    this.elemento = z.elemento;
                    this.imagen = z.imagen;
                    this.meses = z.meses;
                    this.descripcion = z.descripcion;
                  }
                })
              }catch(error){
                  console.error(error)
              }
          },
          mounted(){
            
          }
        }
    }
</script>

<style scoped>
</style>