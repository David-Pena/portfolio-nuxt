<template>
  <div>
    <HomeNavbar />
    <ProjectDetails :project="project" />
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";
import portfolioData from "@/data/portfolio.json";

const route = useRoute();
const project = computed(() => {
  return portfolioData.find((p) => p.id === parseInt(route.params.id)) || null;
});

// Redirect if project not found
watch(project, (newVal) => {
  if (!newVal) {
    navigateTo("/");
  }
});
</script>
