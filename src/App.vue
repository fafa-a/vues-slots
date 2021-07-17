<template>
  <AppUserList :secondrow="(user) => user.phone"> </AppUserList>
</template>

<script setup>
import AppUserList from "./components/AppUserList.vue"
</script>

<style></style>
