<template>
  <div id="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="Site logo">
        <h1>
          Keagan's job list
        </h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import {defineComponent, ref} from "vue";
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'
import JobsList from "./components/JobsList.vue";

export default defineComponent({
  name: 'App',
  components: {
    JobsList
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "Farm worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1"
      },
      {
        title: "Librarian",
        location: "Chimichanga server",
        salary: 25000,
        id: "2"
      },
      {
        title: "Fisherman",
        location: "Lake hylia",
        salary: 21000,
        id: "3"
      },
      {
        title: "Quarryman",
        location: "Death mountain",
        salary: 40000,
        id: "4"
      },
      {
        title: "Prison guard",
        location: "Gerudo valley",
        salary: 32000,
        id: "5"
      }
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return {jobs, handleClick, order}
  }
})
</script>