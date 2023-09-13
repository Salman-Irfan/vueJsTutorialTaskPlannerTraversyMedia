<template>
    <!-- bootstrap form -->
    <form 
    @submit="onSubmit"
    class="mb-3 add-form my-4 mx-4 py-4 px-4 bg-dark text-white">
        <h4 class="text-center">Add Task</h4>
        <div class="form-control my-4 py-4 px-4 bg-dark text-white">
            <!-- task -->
            <div class="mb-3">
                <label class="form-label">Task </label>
                <input
                    type="text"
                    class="form-control"
                    id="addText"
                    placeholder="Task"
                    name="text"
                    v-model="text"
                />
            </div>
            <!-- day and time -->
            <div class="mb-3">
                <label for="dayAndTime" class="form-label">Day & Time</label>
                <input
                    type="datetime-local"
                    class="form-control"
                    id="day"
                    placeholder="Date & Time"
                    name="day"
                    v-model="day"
                />
            </div>
            <!-- reminder -->
            <div class="mb-3 form-check">
                <label
                    class="form-check-label text-success fw-bold h5"
                    for="reminder"
                    >Set Reminder</label
                >
                <input
                    type="checkbox"
                    class="form-check-input"
                    id="reminder"
                    name="reminder"
                    v-model="reminder"
                />
                <!-- submit button -->
                <div class="text-center">
                    <button type="submit" class="btn btn-success">
                        Add Task
                    </button>
                </div>
            </div>
        </div>
    </form>
</template>

<!-- script -->
<script>
// exporting component
export default {
    name: "AddTask",
    // data
    data() {
        return {
            text: "",
            day: "",
            reminder: false,
        };
    },
    // methods
    methods: {
        // onSubmit
        onSubmit(e) {
            e.preventDefault();
            // add form validations
            if (this.text === "") {
                alert("Please enter a task");
                return;
            }
            if (this.day === "") {
                alert("Please enter a date and time");
                return;
            }
            // make a new task
            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            };
            this.$emit('add-task', newTask);
            // reset the form
            this.text = "";
            this.day = "";
            this.reminder = false;

        },
    },
};
</script>
