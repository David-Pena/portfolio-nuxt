<template>
  <div class="resume section-padding pt-0" data-scroll-index="1">
    <div class="sec-head bord-thin-bottom pb-20 mb-80">
      <h4 class="sub-title fz-28">Resume</h4>
    </div>
    <div
      v-for="(item, index) in data.resume"
      :class="`resume-item-container item d-flex align-items-center gap-5 ${
        index !== data.resume.length - 1 ? 'mb-30' : ''
      }`"
      :key="item.id"
    >
      <div class="resume-item-duration date">
        <p class="fz-13">{{ item.duration }}</p>
      </div>
      <div>
        <h6>
          {{ item.company }}
        </h6>
      </div>
      <div class="role ml-auto">
        <p class="fz-13">{{ item.role }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import data from "@/data/info.json";
</script>

<style scoped>
@media (max-width: 768px) {
  .resume-item-container {
    flex-direction: column;
    gap: 10px !important;
  }
  .resume-item-duration {
    margin-right: 0 !important;
  }
  .role {
    margin: 0;
  }
}
</style>
