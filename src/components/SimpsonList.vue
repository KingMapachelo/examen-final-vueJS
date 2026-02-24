<script setup>
import { ref, computed } from 'vue'
import { simpsons } from '@/constants/simpson'
import SimpsonCard from './SimpsonCard.vue'

const search = ref('')
const selectedGender = ref('')

const filteredSimpsons = computed(() => {
  return simpsons.filter((simpson) => {
    const matchesSearch = simpson.name.toLowerCase().includes(search.value.toLowerCase())

    const matchesGender =
      selectedGender.value === '' || simpson.gender.includes(selectedGender.value)

    return matchesSearch && matchesGender
  })
})
</script>

<template>
  <div class="simpsons">
    <SimpsonCard v-for="simpson in filteredSimpsons" :key="simpson.id" :simpson="simpson" />
  </div>
</template>

<style scoped>
.search {
  padding: 10px;
  margin-bottom: 20px;
  width: 300px;
}

.filters {
  margin-bottom: 20px;
}

.filters button {
  margin: 5px;
  padding: 8px 12px;
  cursor: pointer;
}

.active {
  background-color: #e4e006;
  color: white;
}

.simpsons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  justify-content: center;
  gap: 100px;
  margin-top: 20px;
}
</style>
