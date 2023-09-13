<template>
    <header>
        <h1 class="mx-4">{{ title }}</h1>
        <Button  
        @btn-click="$emit('toggle-add-task')"
        :text="showAddTask ? 'Close' : 'Add Task'" 
        :color="showAddTask ? 'red' : '#198754'"/>
    </header>
</template>

<!-- script -->

<script>
// import button
import Button from './Button.vue'
export default {
    name: "Header",
    // props
    props:{
        title: {
            type: String,
            default: "Hello Title"
        },
        showAddTask: Boolean,
    },
    // using button component
    components:{
        Button
    }
};
</script>

<!-- scoped styles -->
<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
        border: 2px solid green;
        margin-top: 2rem;
    }
</style>