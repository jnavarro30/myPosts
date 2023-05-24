<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'
import OrderTerm from './types/OrderTerm';
import JobList from './components/JobsList.vue'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
  //   const state = reactive({
  //     name: 'Link',
  //     age: 25 as number | string,
  //   })
  //   return { ...toRefs(state) }
  // 'link' is string implicityl, added just for consistency
    // const name = ref<string>('Link');
    // const age = ref<number | string>(25)
    // return { name, age }
    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'Lone Ranch', salary: 30000, id: '1' },
      { title: 'coder', location: 'Orange County', salary: 80000, id: '2' },
      { title: 'lawyer', location: 'New York', salary: 100000, id: '3' },
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  },
})
</script>

<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="heart">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<style scoped>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
