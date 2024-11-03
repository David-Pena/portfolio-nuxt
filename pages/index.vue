<template>
  <CommonLoader />
  <HomeLiquid />
  <HomeNavbar />
  <main>
    <HomeMainBox />
    <HomePortfolio />
    <HomeBlog />
    <HomeServices />
  </main>
  <CommonFooter />
</template>

<script setup>
useHead({
  titleTemplate: `%s`,
  bodyAttrs: {
    class: "liquid",
  },
});
</script>
