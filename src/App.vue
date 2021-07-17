<template>
  <AppUserList>
    <template #secondrow="{ item }">
      <a :href="'tel:' + item.phone">{{ item.phone }} </a>
      <br />
      <a :href="'mailto:' + item.email">{{ item.email }} </a>
    </template>
  </AppUserList>
</template>

<script setup>
import AppUserList from "./components/AppUserList.vue"
</script>

<style></style>
