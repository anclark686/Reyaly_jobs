<template>
  <div class="app">
    <header>
      <h1>Reyaly Jobs Post</h1>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    // const name = ref('Link')
    // const age = ref<number | string>(25)

    // return { name, age }
    const jobs = ref<Job[]>([
      {
        title: "farm-worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1",
        description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua",
      },
      {
        title: "quarryman",
        location: "death mountain",
        salary: 40000,
        id: "2",
        description: "Phasellus faucibus scelerisque eleifend donec pretium vulputate sapien",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
        description: "Augue neque gravida in fermentum et sollicitudin ac orci phasellus",
      },
      { title: "fisherman", location: "lake hylia", salary: 21000, id: "4", description: "Massa enim nec dui nunc mattis enim ut",},
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
        description: "Condimentum lacinia quis vel eros",
      },
    ]);

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order };
  },
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #7bbcdb;
    border: 3px solid #7bbcdb;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>
