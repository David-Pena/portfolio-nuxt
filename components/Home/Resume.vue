<template>
  <div class="resume section-padding pt-0" data-scroll-index="1">
    <div class="sec-head bord-thin-bottom pb-20 mb-80">
      <h4 class="sub-title fz-28">Resume</h4>
    </div>
    <div
      v-for="(item, index) in data.resume"
      :class="`item d-flex align-items-center ${
        index !== data.resume.length - 1 ? 'mb-30' : ''
      }`"
      :key="item.id"
    >
      <div class="date mr-60">
        <p class="fz-13">{{ item.duration }}</p>
      </div>
      <div>
        <h6>
          <a href="#0">{{ item.company }}</a>
        </h6>
      </div>
      <div class="ml-auto">
        <div class="d-flex align-items-center">
          <div class="icon-img-40 mr-100">
            <!-- <img :src="item.logo" alt="" /> -->
            <p class="fz-13">{{ item.logo }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
//= Static Data
import data from "@/data/info.json";
</script>
