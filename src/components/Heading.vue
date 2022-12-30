<template>
    <header>
        <div class="flex items-center justify-around">
            <div>
                <h1 class="text-3xl">{{ heading }}</h1>
            </div>
            <div>
                <Button @toggle-add-task='$emit("toggle-add-task")' bg="green" color="white" text="Add New Task"
                    class="mr-3"></Button>
                <!-- <Button bg="red" color="white" text="Update Task" class="mr-3"></Button>
                <Button bg="blue" color="white" text="Delete Task"></Button> -->
            </div>
        </div>
    </header>
</template>

<script>
import Button from './Button.vue';

export default {
    name: "heading",
    props: {
        heading: {
            type: String,
            default: "Hello Vue"
        }
    },
    components: {
        Button,
    },
    emits: ['toggle-add-task']
}
</script>