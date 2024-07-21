<template>
  <div class="author-profile pt-80 pb-80" id="sticky_item" style="position: sticky; top: 25px">
    <div class="cont">
      <div class="img">
        <img src="/assets/imgs/profile-pic-1.jpg" alt="Profile Picture" />
      </div>
      <div class="info text-center mt-30">
        <h5>{{ data.name }}</h5>
        <p>
          <a href="#0">{{ data.username }}</a>
        </p>
      </div>
      <div class="social text-center mt-20">
        <a href="https://x.com/Unans___" target="_blank"><i class="fab fa-twitter"></i></a>
        <a href="https://www.linkedin.com/in/david-pena-avila/" target="_blank"
          ><i class="fab fa-linkedin-in"></i
        ></a>
      </div>
    </div>
  </div>
</template>

<script setup>
//= Static Data
import data from "@/data/info.json";
</script>
