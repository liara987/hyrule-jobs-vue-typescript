<script setup lang="ts">
import { ref } from 'vue'
import JobList from './components/JobList.vue'
import type { JobType } from '@/types/JobType.ts'
import type { OrderTermType } from '@/types/OrderTermType'

const jobs = ref<JobType[]>([
  { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
  { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
  { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
  { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
  { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
])

const order = ref<OrderTermType>('title')

function handleTerm(term: OrderTermType) {
  order.value = term
}
</script>

<template>
  <main>
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="Logo de coração" />
        <h1>Hyryle Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleTerm('title')">Title</button>
        <button @click="handleTerm('salary')">Salary</button>
        <button @click="handleTerm('location')">Location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </main>
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

header .title {
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
