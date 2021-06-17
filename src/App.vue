<template>
  <instruction />
  <div class="main">
    <lead />
    <btn v-on:show-form="displayForm" :showForm="showForm" />
    <formy v-show="showForm" v-on:new-appt="addAppt" />
    <display
      :tasks="tasks"
      v-on:delete-appt="deleteAppt"
      v-on:toggle-appt="toggleAppt"
    />
  </div>
</template>


<script>
import lead from "./components/HelloWorld";
import btn from "./components/button";
import display from "./components/display";
import formy from "./components/formy";
import instruction from "./components/instructions";

export default {
  name: "App",
  components: {
    lead,
    btn,
    display,
    formy,
    instruction,
  },
  data() {
    return {
      tasks: [],
      showForm: false,
    };
  },
  methods: {
    async addAppt(newAppt) {
      const res = await fetch("http://localhost:5000/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(newAppt),
      });
      const data = await res.json();

      this.tasks = [data, ...this.tasks];
    },



    async deleteAppt(id) {
      if (confirm("are you sure you want to delete this appointment?")) {

        const res = await fetch(`http://localhost:5000/tasks/${id}`, {
          method: 'DELETE',
          headers: {
            'Content-type': 'application/json'
          }
        })
          res.status === 200 ? this.tasks = this.tasks.filter((task) => (task.id !== id)) : alert("error deleting appoint");
      }
      return false;
    },
    toggleAppt(id) {
      this.tasks = this.tasks.map((task) =>
        task.id == id ? { ...task, reminder: !task.reminder } : task
      );
      console.log("toggle ready", id);
    },
    displayForm() {
      this.showForm = !this.showForm;
    },
    async fetchAppts() {
      const res = await fetch("http://localhost:5000/tasks");
      const result = res.json();
      return result;
    },
  },
  async created() {
    this.tasks = await this.fetchAppts();
  },
};
</script>




<style scoped>
.main {
  width: 40%;
  height: auto;
  border: 5px solid orangered;
  margin: 70px auto;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

img {
  width: 280px;
  height: 400px;
}

@media screen and (max-width: 500px) {
  .main {
    width: 80%;
  }
  lead {
    color: red;
  }
}
</style>
