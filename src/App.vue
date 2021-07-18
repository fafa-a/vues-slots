<template>
  <AppUserList>
    <template #userList="{ list: users, remove }">
      <AppUserCardsList :list="users">
        <template #secondrow="{ item: user }">
          <AppButton @click="remove(user)">{{ user.name.first }}</AppButton>
        </template>
      </AppUserCardsList>
    </template>
  </AppUserList>
</template>

<script setup>
import AppUserList from "./components/AppUserList.vue"
import AppUserCardsList from "./components/AppUserCardsList.vue"
import AppButton from "./components/AppButton.vue"
</script>

<style></style>
