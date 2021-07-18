<template>
  <AppUserList>
    <template #secondrow="{ remove, item: user }">
      <AppButton @click="remove(user)">{{ user.name.first }}</AppButton>
    </template>
  </AppUserList>
</template>

<script setup>
import AppUserList from "./components/AppUserList.vue"
import AppButton from "./components/AppButton.vue"
</script>

<style></style>
