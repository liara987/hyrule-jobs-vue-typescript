<template>
  <div class="job-list">
    <div>Order by {{ order }}</div>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img src="../assets/rupee.svg" alt="icone de rupees de zelda" />
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Rem omnis voluptatum eius
            doloremque optio iusto sequi dignissimos. Pariatur earum assumenda dolores possimus
            quidem quam, reprehenderit aliquid consequuntur amet non facere.
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script setup lang="ts">
import type { JobType } from '@/types/JobType'
import type { OrderTermType } from '@/types/OrderTermType'
import { computed, toRefs } from 'vue'

const props = defineProps<{
  jobs: JobType[]
  order: OrderTermType
}>()

const { jobs, order } = toRefs(props)

const orderedJobs = computed(() => {
  return [...jobs.value].sort((a: JobType, b: JobType) => {
    return a[order.value] > b[order.value] ? 1 : -1
  })
})
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}

.list-move {
  transition: all 1s;
}
</style>
