<template>
  <section class="blog section-padding" data-scroll-index="5">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="sec-head bord-thin-bottom pb-20 mb-80">
            <h4 class="sub-title fz-28">Blog</h4>
          </div>
        </div>
      </div>
      <div class="row md-marg">
        <div v-for="(item, index) in data" class="col-lg-4" :key="item.id">
          <div :class="`item ${index !== data.length - 1 ? 'md-mb30' : ''}`">
            <div class="img">
              <img :src="item.image" alt="" />
            </div>
            <div class="box">
              <div class="cont">
                <span class="date"
                  ><i class="fas fa-calendar-alt mr-10 main-color"></i> {{ item.date }}</span
                >
                <h5>
                  <a :href="item.url" target="_blank">{{ item.title }}</a>
                </h5>
              </div>
              <div class="info d-flex justify-content-end">
                <div>
                  <span><i class="fas fa-comments fz-12 mr-5"></i> {{ item.comments }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
//= Static Data
import data from "@/data/blog.json";
</script>
