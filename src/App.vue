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
    <Logo :bienvenue="message"/>
    <p>Vue permet de modifier des valeurs en considérant l'interaction utilisateur avec v-on ou @</p>
    <button @click="clicked" id="clicks">
      Clicks: {{ clicks }}
    </button>
    <Logo/>
    <p>Vue permet aussi le 2-way binding, c'est des valeurs affichées en temps réel, qui sont aussi modifiables avec v-model</p>
    <h2>{{ message }}</h2>
    <input v-model="message"/>
    <Logo/>
    <ul id="array-rendering">
      <li v-for="item in items" :key="item.name">
        {{ item.name }} only for {{ item.price }}
      </li>
    </ul>
    <p>Vue permet de créer des composants exportables qui permettent de créer des templates prédéfinis et réutilisables "à l'infini"</p>
    <Logo/>
    <p>Ces composants peuvent comporter des props, c'est à dire des éléments qui varieront en fonction des données qui leur sont attribuées.</p>
    <Logo/>
    <p>Ces props sont assignables à des éléments statiques mais aussi à des variables/éléments dynamiques qui s'afficheront si ils sont définis et qui utiliseront la procédure de fallback définies au préalable (dans le cas où aucune fallback procedure n'est définie, l'élément ne s'affichera tout simplement pas)</p>
    <Logo :bienvenue="message"/>
    <p>Pour effectuer des transferts de données depuis l'enfant vers le parent, l'enfant doit initialiser l'action et le parent en récupérant cette action effectuera la modification de la donnée</p>
    <Logo bienvenue="Un message différent" v-on:sendBounce="squareIt"
    :bounces="bounces"/>
  </div>
</template>

<script>
import Logo from './components/Logo'

export default {
  name: 'App',
  components: {
    Logo,
  },
  data(){
    return {
      counter:0,
      clicks:0,
      message: "Salut !",
      items : [
        { name : 'TV LG15ED56 4K',price:"899€"},
        { name : 'Sony PlayStation 5',price:"599€"},
        { name : 'Xbox Series X',price:"499€"},
        { name : 'Apple iPhone 12',price:"999€"},
        { name : 'Samsung Galaxy S21',price:"899€"},
        { name : 'TV Samsung 1H 4K',price:"999€"},
      ],
      bounces:2,
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
    },
    squareIt(){
      this.bounces = this.bounces*this.bounces;
      return this.bounces;
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
