<template>

    <div v-for="task in tasks" :key="task.id" :class="[task.reminder ? 'reminder' : 'false', task.color ]" v-on:dblclick="toggle(task.id)">
        <h2> {{ task.appointee }} </h2>
        <h5> {{ task.date }} </h5>
        <p> {{ task.purpose }} </p>
        <span class="close" v-on:click="cross(task.id)">❌</span>
    </div>
    
</template>

<script>
    export default {
        name: 'display',
        props: {
            tasks: Array,
        },
        methods: {
            cross(id) {
                    this.$emit('delete-appt', id);
                    console.log(id)
            },
            toggle(id) {
                    this.$emit('toggle-appt', id);
                    console.log(id)
            }
        },
        emits: ['delete-appt', 'toggle-appt']



    }
</script>

<style scoped>
.close {
    color: red;
    float: right;
    position: relative;
    bottom: 40%;
    margin-right: 20px;
    cursor: pointer;
}
div {
    width: 100%;
    height: auto;
    display: block;
    margin: 10px auto 5px;
    padding: 0px 10px;
    border: 2px solid hotpink;
    background-color: pink;
    border-radius: 7px;
}

h2, p {
    line-height: 0px;   
}

.powderblue {
    background-color: powderblue;
    border: 2px solid blue;
}

.wheat {
    background-color: wheat;
    border: 2px solid brown;

}

.greenyellow {
    background-color: greenyellow;
    border: 2px solid green;
}

.reminder {
    border-left: 6px solid green;
}

.false {
    border-left: 6px solid red;
}

</style>