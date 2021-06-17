<template>
    <h1>{{ topic }}</h1>
    <ul>
    <li><h3> {{ ins[0] }}</h3></li>
    <li><h3> {{ ins[1] }} </h3></li>
    <li><h3> {{ ins[2] }} </h3></li>
    </ul>
</template>

<script>

export default {
    name: 'instruction',
    data() {
        return {
            topic: 'INSTRUCTIONS',
            ins: ['Click on the "Add Appt" button to display a form that enables you to input your appointments, appointees, date and color. NB: color must either be powderblue, wheat or greenyellow.',
             'Click the  ❌ sign to delete any appointment fron the appointment tracker.',
             'Doubleclick the divs to toggle the reminders i.e from true to false or vice-versa, which makes the left border green(true) or red(false).'
             ]
        }
    }


}
</script>

<style scoped>

h1 {
    text-decoration: underline;
}

</style>
