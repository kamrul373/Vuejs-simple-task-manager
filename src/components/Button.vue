<template>
    <button @click="toogleAddTask" class="px-5 py-3" :style="{ backgroundColor: bg, color: color }">{{ text }} </button>
</template>


<script>
export default {
    name: "Button",
    props: {
        text: String,
        bg: String,
        color: String
    },
    methods: {
        toogleAddTask() {
            this.$emit("toggle-add-task")
        }
    }
}
</script>