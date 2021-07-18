<template>
  <AppUserList>
    <template #userList="{ list, count }">
      {{ count }}
      <AppUserCardsList :list="list" />
    </template>
  </AppUserList>
</template>

<script setup>
import AppUserList from "./components/AppUserList.vue"
import AppUserCardsList from "./components/AppUserCardsList.vue"
</script>

<style></style>
