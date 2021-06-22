 <template>
  <div id="app" class="d-flex flex-column">
    <div class="align-self-center">
        <router-link class="Enlace" to="/">Home</router-link>
        <router-link class="mx-lg-2 Enlace" to="/signos">Agrupados por Elemento</router-link>
            <b-nav-form>
            <b-form-input
              size="sm"
              class="mr-sm-2"
              placeholder="Search"
              type="text"
              v-model="nombre" >
            </b-form-input >
            <b-button size="sm" class="my-2 my-sm-0" type="submit" v-bind:to="`?nombre=${nombre}`">Search</b-button>
          </b-nav-form>
          <p>{{nombre}}</p>
    </div>
    <router-view />
  </div>
</template>

<script>

export default {
  name: "App",
  components: {
  },
  data() {
    return {
      zodiacos: [],
      nombre: ''
    };
  },
 mounted(){
    console.log('mounted')
  },
  methods:{

  }
};
</script>
<style scoped>
.Enlace{
  color: grey;
  text-decoration: none;
  transition: color 0.5s;
}

.Enlace:hover{
  color: black;
}
</style>
