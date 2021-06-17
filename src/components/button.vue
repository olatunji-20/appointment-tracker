<template>

    <div class="but">
    <button v-text="showForm ? 'Close' : test " v-on:click="onClick()" :class="showForm ? 'red' : color " />
    </div>
</template>

<script>
    export default {
        name: 'btn',
        data() {
            return {
                color: "green",
                test: "Add Appt.",
            }
        },
        methods: {
            onClick() {
                this.$emit('show-form')
            }
        },
        emits: ['show-form'],
        props: {
            showForm: Boolean,
        }
    }
</script>

<style scoped>
.but {
    border: 1px solid black;
    padding: 5px;
    height: 40px;
    width: auto;
}
button {
    color: color;
    width: 100px;
    height: 40px;
    cursor: pointer;
}
.green {
    background-color: green;
    color: #fff;
    border-radius: 8px;
    font-weight: bolder;
    border: 1px solid greenyellow;
}
.red {
    background-color: red;
    color: #ffffff;
    font-weight: bolder;
    border-radius: 8px;
    border: 1px solid greenyellow;
}
</style>