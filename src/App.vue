<template>
  <div id="app" class="container">
    <TodoList></TodoList>
   
  </div>
</template>

<script>

import TodoList from './components/TodoList'

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container{
  max-width: 600px;
  margin: 0 auto;
  
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  /* background: crimson; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
