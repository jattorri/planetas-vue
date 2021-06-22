<template>
  <div class="d-flex flex-wrap col-lg-10 mx-auto my-lg-5">
    <detalle-signo
      v-for="planeta in planetas"
      :key="planeta.id"
      :id="planeta.id"
      :imagen="planeta.urlImg"
      :nombre="planeta.nombre"
      :descripcion="planeta.descripcion"
    />
  </div>
</template>

<script>
import axios from "axios";
import DetalleSigno from "../components/DetalleSigno.vue";
export default {
  name: "Home",
  components: {
    "detalle-signo": DetalleSigno,
  },
  data() {
    return {
      planetas: [],
    };
  },
  methods: {
   async getPlanetas() {
      try {
        let data = await axios.get("http://localhost:8080/test/ta/sistema_solar.json");
        
        this.planetas = data.data;
        let capturados = []
        console.log(this.$route.query.nombre)
        this.planetas.map(z => {
          if(z.nombre.toLowerCase() === this.$route.query.nombre)
          {
          capturados.push(z)
          this.planetas = capturados
          console.log(this.$route.query.nombre)
          }
        });
      } catch (error) {
        console.error(error);
      }
    },
    },
  mounted() {
    this.getPlanetas();
  },
  updated(){
    this.getPlanetas();
  }
};
</script>

<style>
#app {
  height: 100vh;
}
</style>
