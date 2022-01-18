<template>
  <div class="todoapp">
    <TodoHeader :arr="list" @addTask="createTask"></TodoHeader>
    <TodoMain :arr="showArr" @deleteTask="deleteTask"></TodoMain>
    <TodoFooter :arr="showArr" @clearDone="clearDone" @changeSel="changeSel"></TodoFooter>
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
      list: localStorage.getItem('list') ? JSON.parse(localStorage.getItem('list')) : [],
      sel: 'all',
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
    },
    changeSel(sel) {
      this.sel = sel
      console.log(sel);
    },
    clearDone() {
      this.list = this.list.filter(obj => obj.isDone == false)
    }
  },
  computed: {
    showArr() {
      if (this.sel == 'yes') {
        return this.list.filter(obj => obj.isDone == true)
      } else if (this.sel == 'no') {
        return this.list.filter(obj => obj.isDone == false)
      } else if (this.sel == 'all') {
        return this.list
      }
    },

  },
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  },
  watch: {
    list: {
      deep: true,
      handler(newVal) {
        localStorage.setItem('list', JSON.stringify(newVal))
      }
    }
  }
}
</script>

<style>
</style>