<template>
    <div class="mt-4 w-[60%] mx-auto">

        <h2>Tasks</h2>
        <div v-for="task in tasks" class="cursor-pointer">
            <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @deleteTask="$emit('deleteTask', task.id)"
                :key="task.id" :task="task"></Task>
        </div>
    </div>
</template>

<script>
import Task from "./Task.vue";

export default {
    name: "Tasks",
    components: {
        Task,

    },
    props: {
        tasks: Array
    },
    emits: ["deleteTask", "toggle-reminder"]

}
</script>