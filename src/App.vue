<template>
  <select v-model="selected">
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.label }}
    </option>
  </select>
  <AppUserList>
    <template #userList="{ list: users }">
      <AppUserCardsList :list="users">
        <template #[selected]="{ text }">
          <h4>{{ text }}</h4>
        </template>
      </AppUserCardsList>
    </template>
  </AppUserList>
</template>

<script setup>
import AppUserList from "./components/AppUserList.vue"
import AppUserCardsList from "./components/AppUserCardsList.vue"
import AppButton from "./components/AppButton.vue"

ref: selected = "first"
ref: options = [
  { value: "first", label: "first name" },
  { value: "last", label: "last name" },
  { value: "full", label: "full name" },
  { value: "fullWithTitle", label: "full name with title" },
]
</script>

<style></style>
