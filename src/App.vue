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
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: rgb(244, 123, 186);
  background: linear-gradient(-25deg, rgba(244, 123, 186, 0.5) 20%, rgba(90, 95, 245, 0.5) 80%);
  font-family: sans-serif;
}
</style>
