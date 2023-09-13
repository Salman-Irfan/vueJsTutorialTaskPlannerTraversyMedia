<template>
    <div class="container">
        <!-- utlizing header component -->
        <Header
        @toggle-add-task="toggleAddTask"
        title="Task Tracker" 
        :showAddTask="showAddTask"
        />
        <!-- utilizing addTask component -->
        <!-- toggling the add task component -->
        <div v-show="showAddTask">
            <AddTask @add-task="AddTask"/>
        </div>
        <!-- utilizing tasks component -->
        <Tasks
            @toggle-reminder="toggleReminder"
            @delete-task="deleteTask"
            :tasks="tasks"
        />
    </div>
</template>

<script>
// import header, tasks, AddTask
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
    name: "Hello",
    // using components header, tasks
    components: {
        Header,
        Tasks,
        AddTask,
    },
    // data
    data() {
        return {
            tasks: [],
            showAddTask: false
        };
    },
    // methods
    methods: {
        // toggleAddTask
        toggleAddTask() {
            this.showAddTask =!this.showAddTask;
        },
        // add task
        AddTask(task) {
            this.tasks = [...this.tasks, task];
        },
        // delete task
        deleteTask(id) {
            // ask for a warning
            if (confirm("Are you sure you want to delete it?")) {
                this.tasks = this.tasks.filter((task) => task.id !== id);
            }
        },
        // toggle reminder
        toggleReminder(id) {
            this.tasks = this.tasks.map((task) => {
                if (task.id === id) {
                    task.reminder =!task.reminder;
                }
                return task;
            });
        },
    },
    // created
    created() {
        this.tasks = [
            {
                id: 1,
                text: "Doctors Appointment",
                day: "March 1st at 2:30pm",
                reminder: true,
            },
            {
                id: 2,
                text: "Meeting at School",
                day: "March 3rd at 1:30pm",
                reminder: true,
            },
            {
                id: 3,
                text: "Food Shopping",
                day: "March 3rd at 11:00am",
                reminder: false,
            },
        ];
    },
};
</script>

<style scoped>
header {
    line-height: 1.5;
}

@media (min-width: 1024px) {
    header {
        display: flex;
        place-items: center;
        padding-right: calc(var(--section-gap) / 2);
    }
}
</style>
