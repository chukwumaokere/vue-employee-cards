<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h2>Employee Cards</h2>
  <div class="cards">
    <Card />
    <Card />
    <Card />
  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Card
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
.cards{
  display: flex;
  width: 100%;
}
</style>
