<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>Todo App</h1>
    <todo></todo>
  </div>
</template>

<script>
  import Todo from './components/todos'
export default {
  name: 'app',
  components: { Todo }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  display: flex;
  flex-direction: column;
  align-items: center;

}

a {
  color: #42b983;
}

img {
  width: 100px;
}

</style>
