<template>
  <div>
    <h1>Добро пожаловать</h1>

    <button @click="goToLogin">Перейти на страницу входа</button>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'

const router = useRouter()

const goToLogin = (): void => {
  router.push('/login')
}
</script>
