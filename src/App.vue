<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

function goHome() {
  router.push('/')
}
</script>

<template>
  <div id="app">
    <header>
      <h1 @click="goHome" class="logo">Aplicación Simpson</h1>
    </header>

    <main>
      <RouterView />
    </main>
  </div>
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
}

header {
  background: #000000;
  color: white;
  padding: 20px;
}

.logo {
  cursor: pointer;
}

nav a {
  margin: 10px;
  color: #e4d613;
  text-decoration: none;
}

main {
  padding: 20px;
}

footer {
  margin-top: 40px;
  padding: 10px;
  background: #f2f2f2;
}
</style>
