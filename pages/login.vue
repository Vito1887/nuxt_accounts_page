<template>
  <div>
    <h1>Вход</h1>

    <form @submit.prevent="login">
      <input v-model="username" placeholder="Логин" required />

      <input type="password" v-model="password" placeholder="Пароль" required />

      <button type="submit">Войти</button>
    </form>

    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { useUserStore } from "~/store";
import usersData from "~/data/users.json";

const username = ref("");
const password = ref("");
const error = ref("");
const router = useRouter();
const userStore = useUserStore();

const login = () => {
  const user = usersData.find(
    (u) =>
      u.credentials.username === username.value &&
      u.credentials.passphrase === password.value
  );

  if (user) {
    userStore.login();
    router.push("/account");
  } else {
    error.value = "Введены неверные данные авторизации. Попробуйте ещё раз.";
  }
};
</script>
