<template>
  <div>
    <form v-on:submit="onsubmit">
      <input
        type="text"
        placeholder="Appointee"
        v-model="appointee"
        name="appointee"
      />
      <br />
      <input
        type="text"
        placeholder="Purpose"
        v-model="purpose"
        name="purpose"
      />
      <br />
      <input type="date" placeholder="Date" v-model="date" name="date" />
      <!--<input type="text" placeholder="color" v-model="color" name="color" />-->
      <select v-model="color" name="color" class="sel">
        <option value="powderblue">powderblue</option>
        <option value="wheat">wheat</option>
        <option value="greenyellow">greenyellow</option>
      </select>
      <br />
      <input type="checkbox" v-model="reminder" name="reminder" />
      <button type="submit">Submit</button>
    </form>
  </div>
</template>




<script>
export default {
  name: "formy",
  data() {
    return {
      id: "",
      appointee: "",
      purpose: "",
      date: "",
      color: "",
      reminder: false,
    };
  },
  methods: {
    onsubmit(e) {
      e.preventDefault();

      if (!this.appointee) {
        alert(
          "please input the name of the person you fixed an appointment with"
        );
        return;
      }

      const newAppt = {
        id: Math.floor(Math.random() * 1000),
        appointee: this.appointee,
        purpose: this.purpose,
        date: this.date,
        color: this.color,
        reminder: this.reminder,
      };

      console.log(newAppt);

      {
        (this.id = ""),
          (this.appointee = ""),
          (this.purpose = ""),
          (this.date = ""),
          (this.color = ""),
          (this.reminder = false);
      }
      this.$emit("new-appt", newAppt);
    },
  },
  emits: ["new-appt"],
};
</script>




<style scoped>
div {
  width: 100%;
  height: auto;
  background-color: #ffffff88;
  border: 1px solid black;
  padding: 20px 10px;
  text-align: center;
  margin: 20px auto;
}

input,
.sel {
  background-color: #e6e6e6;
  height: 30px;
  width: 95%;
  margin: 5px auto;
  text-indent: 10px;
  border-radius: 5px;
  border: 0px solid black;
}

button {
  width: 40%;
  height: 35px;
  background-color: green;
  margin: 10px auto 0px;
  border-radius: 5px;
  color: white;
}
</style>
