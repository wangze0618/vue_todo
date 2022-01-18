<template>
    <header class="header">
        <h1>todos</h1>
        <input id="toggle-all" class="toggle-all" type="checkbox" />
        <label for="toggle-all"></label>
        <input
            class="new-todo"
            type="text"
            placeholder="输入任务名称-回车确认"
            autofocus
            @keydown.enter="add"
            v-model="task"
        />
    </header>
</template>

<script>
export default {
    data() {
        return {
            task: ''
        }
    },
    methods: {
        add() {
            this.$emit('addTask', this.task)
            this.task = ''
        }
    }

}
</script>