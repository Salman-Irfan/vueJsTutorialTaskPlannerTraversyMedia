<template>
    <button
        @click="onClick()"
        :style="{ backgroundColor: color }"
        class="btn btn-success mx-4"
    >
        {{ text }}
    </button>
</template>

<!-- script -->
<script>
export default {
    name: "Button",
    // props
    props: {
        text: {
            type: String,
            default: "lorem ipsum",
        },
        color: {
            type: String,
            default: "primary",
        },
    },
    // methods
    methods: {
        // onClick:
        onClick() {
            this.$emit('btn-click');
        },
    },
};
</script>
