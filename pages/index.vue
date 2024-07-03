<template>
  <CommonLoader />
  <PreviewNavbar />
  <main>
    <PreviewMainBox />
  </main>
  <CommonFooter />
</template>

<script setup>
//= Page Metadata
definePageMeta({
  layout: 'preview'
});
//= Page Head
useHead({
  titleTemplate: `%s - Preview`
})
</script>


<style>
body {
  background: #222
}
</style>