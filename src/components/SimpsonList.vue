<script setup>
import { ref, onMounted } from 'vue'
import SimpsonCard from './SimpsonCard.vue'

const simpsons = ref([])

const getSimpsons = async () => {
  try {
    const response = await fetch('https://thesimpsonsapi.com/api')
    const data = await response.json()

    simpsons.value = data.docs
  } catch (error) {
    console.error('Error al obtener datos:', error)
  }
}

onMounted(getSimpsons)
</script>

<template>
  <div>
    <div class="simpsons">
      <SimpsonCard v-for="simpson in simpsons" :key="simpson._id" :simpson="simpson" />
    </div>
  </div>
</template>

<style scoped>
.simpsons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  justify-content: center;
  gap: 100px;
  margin-top: 20px;
}
</style>
