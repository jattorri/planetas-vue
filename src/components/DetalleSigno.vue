<template>
    <div class="card ml-lg-1 my-lg-1 py-lg-1">
      <div>
          <img class="img-thumbnail img-responsive" v-bind:src="imagen" />
          <p class="ml-lg-1">Planeta: <b>{{nombre}}</b></p>
      </div>
      <div class="text-center">
        <router-link class="btn btn-outline-primary"  v-bind:to="`/signo/${id}`">
          VER DETALLE
        </router-link>
      </div>
    </div>

</template>

<script>
export default {
  name: "DetalleSigno",
  props: {
    id: Number,
    nombre: String,
    elemento: String,
    imagen: String,
    meses: [],
    descripcion: String,
  },
  methods:{
  },
  data(){
    return{
      props: undefined
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
