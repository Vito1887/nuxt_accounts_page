<template>
  <div>
    <h1>Добро пожаловать</h1>

    <button @click="goToLogin">Перейти на страницу входа</button>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const goToLogin = () => {
  router.push('/login')
}
</script>
