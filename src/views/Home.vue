<script setup lang="ts">
import {  ref } from 'vue'

defineOptions({
  name: 'HomeView'
})

const name = ref('')
const lastName = ref('McDonnell')

const handleSubmit = () => {
  console.log(name.value + ' ' + lastName.value)
}

</script>

<template>
  <div class="container">
    <h1>Form Demo Playground</h1>

<form @submit.prevent="handleSubmit" class="form-wrapper">
    <label for="name">Name</label>
    <input type="text" id="name" v-model="name" />
    <button type="submit">Submit</button>
  </form>
  </div>
</template>

<style lang="css">
body {
  background-color: #353535;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #353535;
  color: #ffff;
}

.form-wrapper {
  display: flex;
  flex-direction: column;
  gap: 15px;
  min-width: 40%;
}
</style>
