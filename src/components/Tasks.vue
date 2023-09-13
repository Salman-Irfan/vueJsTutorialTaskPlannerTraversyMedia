<template>
    <div :key="task.id" v-for="task in tasks">
        <!-- utilizing Task Component here -->
        <Task 
        @toggle-reminder="$emit('toggle-reminder', task.id)" 
        @delete-task="$emit('delete-task', task.id)" 
        :task="task"/>
    </div>
</template>

<script>
// importing Task
import Task from "./Task.vue";
export default {
    name: "Tasks",
    props: {
        tasks: Array,
    },
    // registering Task as Component
    components: {
        Task,
    },
    // defining emits
    emits: ["delete-task", "toggle-reminder"],
};
</script>
