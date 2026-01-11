<script setup lang="ts">
import { ref } from 'vue';

const name = ref('');

const handleSubmit = () => {
    console.log(name.value);
}
</script>

<template>
    <form @submit.prevent="handleSubmit">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="name" />
    </form>
</template>