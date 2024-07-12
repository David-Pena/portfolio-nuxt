<template>
  <div class="about section-padding" data-scroll-index="0">
    <div class="cont">
      <h1>
        Hello, I’m <span class="main-color">David Peña</span>, Front-end Developer Based in LA.
      </h1>
    </div>
    <div class="stauts mt-80">
      <div class="d-flex align-items-center">
        <div class="mr-40">
          <div class="d-flex align-items-center">
            <h2>{{ data.years_of_experance }}</h2>
            <p>
              Years <br />
              of Experience
            </p>
          </div>
        </div>
        <div>
          <div class="butn-presv">
            <a
              href="https://docs.google.com/document/d/1f51yzqyQlJd_OIALshKrMklQkSWPR3gE9xowl3cimHo/edit?usp=sharing"
              target="blank"
              class="butn butn-md butn-bord radius-5 skew"
            >
              <span>Download C.V</span>
            </a>
          </div>
        </div>
      </div>
    </div>
    <div class="text mt-80">
      <h6 class="sub-title mb-15">About Me.</h6>
      <p class="fz-20">{{ data.brief }}</p>
    </div>
  </div>
</template>

<script setup>
//= Static Data
import data from "@/data/info.json";
</script>
