<template>
    <form @submit="handleAddTaskSubmit" class="mb-4 mx-auto pl-[180px] pt-8">
        <input type="text" placeholder="Task name" v-model="name">
        <input type="text" placeholder="Date" v-model="date">
        <div class="flex mb-5">
            <label for="reminder">Set Reminder</label>
            <input type="checkbox" id="reminder" v-model="reminder">
        </div>
        <input type="submit" value="Add Task" class="cursor-pointer">
    </form>
</template>


<script>
export default {
    name: "AddTask",
    data() {
        return {
            name: "",
            date: "",
            reminder: ""
        }
    },
    methods: {
        handleAddTaskSubmit(e) {
            e.preventDefault();
            if (!this.name) {
                return alert("Please write a task name")
            }
            const newTask = {
                id: Math.floor(Math.random() * 10000),
                "text": this.name,
                "day": this.date,
                "reminder": this.reminder
            }
            this.$emit("AddTask", newTask)
            this.name = ""
            this.date = ""
            this.reminder = false
        }
    }
}
</script>

<style scoped>
input {
    display: block;
    width: 440px;
}

input[type='text'] {
    border: 1px solid grey;
    padding: 10px 20px 10px 5px;
    margin-bottom: 10px;
}

input[type="submit"] {
    background-color: black;
    color: white;
    padding: 10px;
}
</style>