<template>
    <div id="app">
        <Fact v-bind:fact="fact"/>
    </div>
</template>

<script>
import Fact from './components/Fact.vue'

export default {
  name: 'App',
  components: {
    Fact
  },
  data() {
        return {
            fact: {}
        }
  },
  methods: {
    getFact() {
        this.axios
            .get('http://188.225.47.187/api/cats/random-fact.php')
            .then((response) => {this.fact = response.data})
    }
  },
  mounted() {
    this.getFact();
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
