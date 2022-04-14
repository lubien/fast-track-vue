<template>
  <div id="app">
    <h1>Tarefas</h1>

    <ul>
      <li v-for="task in tasks" :key="task">
        {{task}}

        <button @click="deleteTask(task)">Apagar</button>
      </li>
    </ul>

    <input type="text" v-model="newTask" @keypress.enter="addTask">
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: ['Finalizar curso']
    }
  },
  methods: {
    addTask() {
      if (this.newTask.length === 0) { return }
      this.tasks.push(this.newTask)
      this.newTask = ''
    },

    deleteTask(task) {
      this.tasks = this.tasks.filter(t => t !== task)
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
