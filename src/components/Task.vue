<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" 
    :class="[task.reminder ? 'reminder task' : 'task']">
        <h3>
            <i @click="$emit('delete-task',task.id)" class="fas fa-times px-4"></i>
            {{ task.text }}
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<!-- script -->
<script>
export default {
    name: "Tasks",
    // props
    props: {
        task: Object,
    },
};
</script>

<!-- style -->

<style scoped>
.task {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-bottom: 10px;

    h3 {
        margin: 0;
    }
}
.task:hover {
    background-color: #eee;
}
.task.reminder {
    border-left: 5px solid #198754;
}

.fas {
    color: red;
}
.fas:hover {
    color: rgb(221, 15, 15);
    cursor: pointer;
    transform: scale(1.2);
}
@media screen and (max-width: 425px) {
    .task {
        display: block;
    }

    h3 {
        flex: 1; /* Allow h3 to take up remaining horizontal space */
        font-size: 18px;
        font-weight: bolder;
    }

    p {
        margin-top: 10px; /* Add margin to separate p from h3 on larger screens */
        font-size: 12px;
        text-align: center;
    }
}
</style>
