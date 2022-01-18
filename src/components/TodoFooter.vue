<template>
    <footer class="footer">
        <span class="todo-count">
            剩余:
            <strong>{{ this.arr.length }}</strong>
        </span>
        <ul class="filters">
            <li>
                <a :class="{ selected: isSel == 'all' }" @click="s1" href="javascript:;">全部</a>
            </li>
            <li>
                <a :class="{ selected: isSel == 'no' }" @click="s2" href="javascript:;">未完成</a>
            </li>
            <li>
                <a :class="{ selected: isSel == 'yes' }" @click="s3" href="javascript:;">已完成</a>
            </li>
        </ul>
        <button class="clear-completed" @click="clear()">清除已完成</button>
    </footer>
</template>

<script>

export default {
    data() {
        return {
            isSel: 'all'
        }
    },
    methods: {
        s1() {
            this.isSel = 'all'
            this.$emit('changeSel', this.isSel)
        },
        s2() {
            this.isSel = 'no'
            this.$emit('changeSel', this.isSel)
        },
        s3() {
            this.isSel = 'yes'
            this.$emit('changeSel', this.isSel)
        },
        clear() {
            this.$emit('clearDone')
        }

    },
    props: ['arr']
}
</script>