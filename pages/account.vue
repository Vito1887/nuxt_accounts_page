<template>
  <div>
    <h1>Аккаунт</h1>

    <button @click="logout">Выход</button>

    <table>
      <thead>
        <tr>
          <th>Имя</th>

          <th>Фамилия</th>

          <th>Логин</th>

          <th>Дата создания</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="user in users" :key="user.credentials.username">
          <td>{{ user.name }}</td>

          <td>{{ user.surname }}</td>

          <td>{{ user.credentials.username }}</td>

          <td>{{ user.created }}</td>
        </tr>

      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useUserStore } from "~/store";
import usersData from "~/data/users.json";

interface User {
  name: string;
  surname: string;
  credentials: {
    username: string;
  };
  created: string;
}

const users = ref<User[]>(usersData);
const userStore = useUserStore();

const logout = (): void => {
  userStore.logout();
  window.location.href = "/login";
};
</script>
