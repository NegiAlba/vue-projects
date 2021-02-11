<template>
  <div id="app">
    <h1>Intro à Vue.js</h1>
    <p>Vue permet d'afficher des données dynamiques comme un compteur avec les moustaches</p>
    <img src="./assets/moustache.png" alt="" srcset="">
    <div id="counter">
      Counter : {{ counter }}
    </div>
    <p>Vue permet aussi de l'affichage conditionnel avec v-if</p>
    <div id="conditional">
      <span v-if="clicks>10">Calme-toi stp</span>
      <div v-if="clicks>100">Mec respire wtf</div>
    </div>
    <p>Vue permet de modifier des valeurs en considérant l'interaction utilisateur avec v-on ou @</p>
    <button @click="clicked" id="clicks">
      Clicks: {{ clicks }}
    </button>
    <p>Vue permet aussi le 2-way binding, c'est des valeurs affichées en temps réel, qui sont aussi modifiables avec v-model</p>
    <h2>{{ message }}</h2>
    <input v-model="message"/>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return {
      counter:0,
      clicks:0,
      message: "Salut !",
    }
  },
  mounted() {
    setInterval(() =>{
      this.counter++
    },100)
  },
  methods : {
    clicked(){
      this.clicks++;
    }
  }
}
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
</style>
