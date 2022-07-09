<template>
<!--img alt="Vue logo" src="./assets/logo.png"-->
<div id="app">
  <todo-app></todo-app>
</div>
  <TodoList msg="ToDo App"/>
</template>

<script>
import TodoList from './components/TodoList.vue'


export default {
  name: 'App',
  components: {
    TodoList
  },
}
</script>

<style>

</style>