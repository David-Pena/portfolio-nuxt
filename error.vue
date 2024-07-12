<template>
  <div class="error-page">
    <h1>{{ statusCode === 404 ? "Page not found" : "Oops, something went wrong!" }}</h1>
    <p>{{ error.message }}</p>
    <button class="button" @click="goBack"><span class="text">Go back</span></button>
  </div>
</template>

<script setup>
const props = defineProps({
  error: {
    type: Object,
  },
});

const router = useRouter();

function goBack() {
  router.replace("/");
}
</script>

<style scoped>
.error-page {
  text-align: center;
  margin: 50px auto;
}
</style>
