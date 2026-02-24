<script setup>
import { useRouter } from 'vue-router'

const props = defineProps({
  simpson: Object,
})

const router = useRouter()

const rutaImg = 'https://cdn.thesimpsonsapi.com/200'

function goToDetail() {
  router.push(`/simpson/${props.simpson.id}`)
}
</script>

<template>
  <div class="card" @click="goToDetail">
    <img :src="`${rutaImg}${simpson.portrait_path}`" alt="Imagen" />
    <h3>{{ simpson.name }}</h3>
  </div>
</template>

<style scoped>
.card {
  cursor: pointer;
  text-align: center;
  transition: transform 0.2s ease;
}

.card:hover {
  transform: scale(1.05);
}

.card img {
  width: auto;
  height: auto;
  object-fit: cover;
  border-radius: 12px;
  background-color: white;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.card h3 {
  margin-top: 10px;
  font-size: 20px;
}
</style>
