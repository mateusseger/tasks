<template>
  <div id="app">
    <TaskProgress :progress="progress"/>
    <NewTask @newTask="taskAdd" />
    <TaskPanel :tasks="tasks" 
      @taskRemove="taskRemove"
      @taskChangeState="taskChangeState" />
  </div>
</template>

<script>
import TaskProgress from '@/components/TaskProgress'
import NewTask from '@/components/NewTask'
import TaskPanel from '@/components/TaskPanel'

export default {
  name: 'App',
  components: {
    TaskProgress,
    NewTask,
    TaskPanel
  },
  data() {
    return {
      tasks: []
    }
  },
  computed: {
    progress() {
      const total = this.tasks.length
      const done = this.tasks.filter(t => t.status).length
      return Math.round(done / total * 100) || 0
    }
  },
  watch: {
    tasks: {
      deep: true, //monitora de forma profunda os elementos
      handler() {
        localStorage.setItem('tasks', JSON.stringify(this.tasks))
      }
    }
  },
  methods: {
    taskAdd(newTask) {
      const sameName = task => task.desc === newTask
      const reallyNew = this.tasks.filter(sameName).length == 0

      if (reallyNew) {
        this.tasks.push({
          desc: newTask,
          status: false
        })
      } else {
        alert('Tarefa já registrada!')
      } 
    },
    taskRemove(i) {
      this.tasks.splice(i, 1)
    },
    taskChangeState(i) {
      this.tasks[i].status = !this.tasks[i].status
    }
  },
  created() {
    const json = localStorage.getItem('tasks')
    const array = JSON.parse(json)
    this.tasks = Array.isArray(array) ? array : []
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#app p, span {
  color: #fff;
}
</style>
