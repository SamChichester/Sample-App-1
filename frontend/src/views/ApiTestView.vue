<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import LoadingSpinner from '@/components/LoadingSpinner.vue';

const message = ref('');
const loading = ref(false);
const errorMessage = ref('');

const fetchMessage = async () => {
  errorMessage.value = '';
  loading.value = 'true';

  try {
    const response = await axios.get("https://backend.paas.samchichester.com/messages");
    message.value = response.data;
  } catch (err) {
    console.error('Error: ', err);
    errorMessage.value = 'Failed to fetch message.';
  } finally {
    loading.value = false;
  }
}

onMounted(() => {
  fetchMessage();
})
</script>

<template>
  <div class="container mx-auto mt-3">
    <h1 class="text-3xl font-bold text-center mb-4">API Test Page</h1>
    <div class="flex items-center justify-center" v-if="loading">
      <LoadingSpinner />
    </div>
    <div v-else-if="errorMessage" class="text-red-500 text-center">{{ errorMessage }}</div>
    <div v-else>
      {{ message }}
    </div>
  </div>
</template>