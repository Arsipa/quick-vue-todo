<template>
<div class="wrapper">
  <h1>TODO</h1>
  <button class="create" @click="createTask">create task</button>
  <ul>
    <listItem 
      v-for="(task, index) in tasks" 
      :task="task"
      :key="index" 
      @apply="(newValue) => updateTask(index, newValue)" 
      @delete="deleteTask(index)"
    />
  </ul>
</div>
</template>

<script>
import listItem from './components/listItem.vue'

export default {
  name: 'App',
  components: {
    listItem
  },
  data() {
    return {
      tasks: [
        "Покакать",
        "Пописить",
        "Анжумания",
        "Пресс качат",
        "Бегит",
      ],
    }
  },
  methods: {
    updateTask(index, newValue) {
      this.tasks[index] = newValue;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    createTask() {
      this.tasks.push(prompt('task name'))
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  text-align: center;
  padding: 50px 0;
}
.create {
  padding: 20px;
  font-size: 20px;
  color: white;
  background: blue;
  border-radius: 10px;
}
ul {
  padding: 30px 0;
}
</style>
