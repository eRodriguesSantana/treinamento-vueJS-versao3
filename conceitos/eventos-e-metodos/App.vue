<template>
  <div>
    <h1>Minha lista de tarefas</h1>

    <button @click="handleShowHideList">Ver a lista</button>

    <br />

    <input type="text" v-focus v-model="currentTask" v-on:keyup.enter="addTask"/>

    <ul v-if="showList">
      <li 
        v-for="(task, index) in tasks" 
        v-bind:key="`${task}-${index}`"
        v-on:dblclick="complete(task)"
        v-bind:class="{'line-through': task.isDone}"
        class="task-item"
      >
        {{ task.name }}
        <button v-on:click="remove(task)">&times;</button>
      </li>
    </ul>

    <p v-else>Lista de tarefas escondidas</p>
  </div>
</template>

<script>
const focus = {
  inserted: (el) => {
    el.focus();
  },
};
export default {
  directives: {
    focus,
  },
  data: () => ({
    currentTask: '',
    showList: false,
    tasks: [{ name: "Fazer o curso", isDone: false }],
  }),
  methods: {
    handleShowHideList() {
      this.showList = !this.showList
    },
    remove(task) {
      this.tasks = this.tasks.filter(t => t.name !== task.name)
    },
    complete(task) {
      this.tasks = this.tasks.map(t => {
        if(t.name === task.name) {
          return { ...t, isDone: !t.isDone }
        }
        return { ...t.name }
      })
    },
    addTask() {
      this.tasks.push({
        name: this.currentTask,
        isDone: false
      })
      this.currentTask = ''
    }
  }
};
</script>

<style scoped>
.line-through {
  text-decoration: line-through;
}

.task-item {
  cursor: pointer;
}
</style>