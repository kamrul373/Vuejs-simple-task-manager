<template>
    <div @dblclick="$emit('toggle-reminder', task.id)"
        :class="[task.reminder ? 'reminder' : '', 'task flex justify-between items-center']">
        <div>
            <h2>{{ task.text }}</h2>
            <p>{{ task.day }}</p>
        </div>
        <i @click="deleteTask(task.id)" class="fas fa-times text-xl cursor-pointer"></i>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object,
    },
    methods: {
        deleteTask(id) {
            this.$emit("deleteTask", id)
        },

    }
}
</script>

<style scoped>
.task {
    background-color: gainsboro;
    margin-bottom: 20px;
    padding: 20px 20px 20px 10px;
}

.fa-times {
    color: red
}

.reminder {
    border-left: 6px solid green;
}
</style>