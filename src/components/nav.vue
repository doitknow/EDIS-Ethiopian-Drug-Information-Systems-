<script setup>
import navs from "@/config/nav.js";
import { useAuthStore } from "@/stores/auth";

const authStore = useAuthStore();

const filteredNavs = navs.filter(
  (nav) => !nav.hideFor?.includes(authStore.auth?.roleName)
);
</script>

<template>
  <ul>
    <li v-for="nav in filteredNavs" :key="nav.path">
      <RouterLink :to="nav.path">
        <span>{{ nav.name }}</span>
      </RouterLink>
    </li>
  </ul>
</template>
