<template>
  <section>
    <slot name="title">Users</slot>
    <slot
      name="userList"
      :count="data.results.length"
      :list="data.results"
      v-if="state === 'loaded'"
    >
      <ul class="userlist">
        <li v-for="item in data.results" :key="item.email">
          <slot name="listItem" :user="item">
            <div>
              <img
                width="48"
                height="48"
                :src="item.picture.large"
                :alt="item.name.first + ' ' + item.name.last"
              />
              <div>
                <div>{{ item.name.first }}</div>
                <slot name="secondrow" :item="item"></slot>
              </div>
            </div>
          </slot>
        </li>
      </ul>
    </slot>
    <slot v-if="state === 'loading'" name="loading"> loading... </slot>
    <slot v-if="state === 'failed'" name="error"
      >Oops something went wrong.</slot
    >
  </section>
</template>

<script setup>
const AllStates = {
  idle: "idle",
  loading: "loading",
  loaded: "loaded",
  failed: "failed",
}
ref: state = "idle"
ref: data = undefined
ref: error = undefined
ref: states = AllStates

onMounted(() => {
  load()
})

const load = async () => {
  state = "loading"
  error = undefined
  data = undefined
  try {
    const response = await fetch("https://randomuser.me/api/?results=5")
    const json = await response.json()
    state = "loaded"
    data = json
    return response
  } catch (err) {
    state = "failed"
    error = err
    return error
  }
}
</script>

<style>
.userlist {
  margin: 10px;
}
.userlist img {
  border-radius: 50%;
  margin-right: 1rem;
}
.userlist li + li {
  margin-top: 10px;
}
.userlist li > div {
  display: flex;
  align-items: center;
}
.userlist li div div {
  flex: 1;
}
</style>
