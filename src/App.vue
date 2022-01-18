<template>
  <div class="todoapp">
    <TodoHeader @addTask="createTask"></TodoHeader>
    <TodoMain :arr="this.list" @deleteTask="deleteTask"></TodoMain>
    <TodoFooter :arr="this.list"></TodoFooter>
  </div>
</template>

<script>
import './styles/base.css'
import './styles/index.css'
import TodoHeader from "./components/TodoHeader";
import TodoMain from "./components/TodoMain";
import TodoFooter from "./components/TodoFooter";
export default {
  data() {
    return {
      list: [
        { id: 100, name: "吃饭", isDone: true },
        { id: 101, name: "睡觉", isDone: false },
        { id: 102, name: "打豆豆", isDone: true },
      ],
    }
  },
  methods: {
    createTask(task) {
      let id = this.list.length == 0 ? 100 : this.list[this.list.length - 1].id + 1
      this.list.push({
        id: id,
        name: task,
        isDone: false
      })
    },
    deleteTask(index) {
      this.list.splice(index, 1)
    }
  },
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  }
}
</script>

<style>
</style>