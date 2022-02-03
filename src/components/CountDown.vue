<template>
  <h1>{{ title }}</h1>
  <div :class="{ aboveTen: this.number > 10, tenOrBelow: this.number <= 10 }">
    {{ time }}
  </div>
  <br />
  <!-- <div v-if="this.number % 2 == 0">This is visible only on even number</div> -->
  <input type="text" name="bla" v-model="number" />
  <button class="btn btn-primary" @click="updateNumber">Speed up</button>
  <br />
  <div v-for="user in users" :key="user.name">
    User {{ user.name }} is {{ user.age }} years old
  </div>
</template>

<script>
export default {
  name: "CountDown",
  data() {
    return {
      number: 20,
      time: "",
      names: ["Jack", "John", "Alice", "Fatima"],
      users: [
        {
          name: "Jack Monterrey",
          age: 53,
        },
        {
          name: "John Daniels",
          age: 12,
        },
      ],
    };
  },
  methods: {
    updateNumber() {
      this.number -= 1;
      if (this.number < 0) this.number = 20;
    },
    displayTime() {
      this.time = new Date(this.number * 1000).toISOString().substr(11, 8);
    },
  },
  mounted() {
    setInterval(() => {
      this.updateNumber();
      this.displayTime();
    }, 1000);
  },
};
</script>

<style>
.aboveTen {
  font-size: 100px;
  margin: 50px 600px;
  color: green;
  background-color: lavender;
  border: solid 1px black;
}

.tenOrBelow {
  font-size: 100px;
  margin: 50px 600px;
  color: red;
  background-color: lavender;
  border: solid 1px black;
}
</style>