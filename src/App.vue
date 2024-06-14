<template>
  <div class="score">
    <p>Puntaje: {{ puntaje }}</p>
    <p>Intento: {{ intento }}</p>
  </div>
  <div class="hijo">
    <Hijo :texto="dato1" :img="imagen1" />
    <Hijo :texto="dato2" :img="imagen2" />
    <Hijo :texto="dato3" :img="imagen3" />
  </div>

  <button @click="jugar()">JUGAR</button>
</template>

<script>
import Hijo from "@/components/Hijo.vue";

export default {
  name: "App",
  components: {
    Hijo,
  },
  data() {
    return {
      imagen1: "https://via.placeholder.com/250",
      imagen2: "https://via.placeholder.com/250",
      imagen3: "https://via.placeholder.com/250",
      dato1: "xxxxxxxxxxx",
      dato2: "xxxxxxxxxxx",
      dato3: "xxxxxxxxxxx",
      puntaje: 0,
      intento: 0,
      names: [],
      images:[],
      pokemon:[],
    };
  },
  methods: {
    getRandomInt(max) {
      return Math.floor(Math.random() * max);
    },

    async jugar() {
      
      await this.obtenerPokemon();
      
    },
    async obtenerPokemon() {
      var aux =[];
        for (let i = 0; i <= 5; i++) {
          aux.push
          const {name} = await fetch(`https://pokeapi.co/api/v2/pokemon/${i+1}`).then(r => r.json());
          
          console.log(name)
          this.names.push(name)
         this.images.push(`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${i+1}.svg`)
         console.log(this.images[i])
      }
      
       this.imagen1 =  this.images[this.getRandomInt(5)];
      this.imagen2 =  this.images[this.getRandomInt(5)];
      this.imagen3 =  this.images[this.getRandomInt(5)];
      this.dato1 = this.names[this.getRandomInt(5)];
      this.dato2 = this.names[this.getRandomInt(5)];
      this.dato3 = this.names[this.getRandomInt(5)];      
    },
    verificar(e) {
      
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.score {
  display: grid;
  grid-template-columns: repeat(2, 550px);
  justify-content: center;
}
.hijo {
  display: grid;
  grid-template-columns: repeat(3, 450px);
}
</style>
