<script setup>
import Heading from './components/Heading.vue';
import Tasks from "./components/Tasks.vue"
import AddTask from "./components/AddTask.vue";

</script>

<template>
  <main class="max-w-[920px] mx-auto pt-8">
    <Heading @toggle-add-task="toggleAddTask" heading="Task Manager"></Heading>
    <div v-if="toggleForm">
      <AddTask @AddTask="addTask"></AddTask>
    </div>

    <Tasks @toggle-reminder="handleToggle" @deleteTask="delTask" :tasks="tasks"></Tasks>
  </main>
</template>

<script>

export default {
  name: "App",
  components: {
    Heading,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      toggleForm: false
    }
  },
  methods: {
    toggleAddTask() {
      return this.toggleForm = !this.toggleForm
    },
    addTask(task) {
      return this.tasks.push(task)
    },
    delTask(id) {
      if (confirm("Are you sure you want to delete ?")) {
        this.tasks = this.tasks.filter(task => task.id !== id)
      }
    },
    handleToggle(id) {
      this.tasks = this.tasks.map(task => task.id === id ? { ...task, reminder: !task.reminder } : task)
      console.log(this.tasks)
    }
  },
  created() {
    {
      this.tasks = [
        {
          "id": "1",
          "text": "Doctors Appointment",
          "day": "March 5th at 2:30pm",
          "reminder": true
        },
        {
          "id": "2",
          "text": "Meeting with boss",
          "day": "March 6th at 1:30pm",
          "reminder": true
        },
        {
          "id": "3",
          "text": "Food shopping",
          "day": "March 7th at 2:00pm",
          "reminder": false
        }
      ]
    }
  }

}
</script>

