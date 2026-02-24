<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const simpson = ref(null)

const rutaImagen = 'https://cdn.thesimpsonsapi.com/200'

onMounted(async () => {
  const id = route.params.id

  const response = await fetch(`https://thesimpsonsapi.com/api/characters/${id}`)

  const data = await response.json()
  simpson.value = data
})
</script>

<template>
  <div v-if="simpson">
    <img :src="`${rutaImagen}${simpson.portrait_path}`" alt="Imagen" />
    <p><strong>Edad:</strong> {{ simpson.age }}</p>
    <p><strong>Fecha de nacimiento:</strong> {{ simpson.birthdate }}</p>
    <p><strong>Descripción:</strong> {{ simpson.description }}</p>
    <p><strong>Género:</strong> {{ simpson.gender }}</p>
    <p><strong>Nombre:</strong> {{ simpson.name }}</p>
    <p><strong>Trabajo:</strong> {{ simpson.occupation }}</p>
    <p><strong>Frases:</strong>{{ simpson.phrases }}</p>
    <p><strong>Estado:</strong>{{ simpson.status }}</p>
  </div>

  <div v-else>Cargando...</div>
</template>

<style scoped></style>
