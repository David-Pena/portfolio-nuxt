<template>
  <section class="portfolio section-padding pt-0" data-scroll-index="3">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="sec-head bord-thin-bottom pb-20 mb-30">
            <h4 class="sub-title fz-28">Portfolio</h4>
          </div>
        </div>
      </div>
      <div class="row">
        <div v-for="item in topTwo" class="col-lg-6" :key="item.id">
          <div class="item mt-50">
            <div class="img">
              <NuxtLink :to="`/project/${item.id}`">
                <img :src="item.image" alt="" class="radius-5" />
              </NuxtLink>
            </div>
            <div class="cont mt-30">
              <div>
                <span class="tag">{{ item.category }}</span>
                <h6 class="line-height-1">
                  <NuxtLink :to="`/project/${item.id}`">{{ item.title }}</NuxtLink>
                </h6>
                <p class="mt-15 fz-15">{{ item.brief }}</p>
                
                <!-- Add tech stack preview -->
                <div class="tech-preview mt-15">
                  <span v-for="tech in item.techStack.slice(0, 3)" 
                        :key="tech" 
                        class="tech-tag">
                    {{ tech }}
                  </span>
                </div>
              </div>
              <div class="d-flex align-items-center mt-20">
                <div class="ml-auto">
                  <div class="arrow">
                    <NuxtLink :to="`/project/${item.id}`">
                      <svg class="arrow-right" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 34.2 32.3">
                        <line x1="0" y1="16" x2="33" y2="16"></line>
                        <line x1="17.3" y1="0.7" x2="33.2" y2="16.5"></line>
                        <line x1="17.3" y1="31.6" x2="33.5" y2="15.4"></line>
                      </svg>
                    </NuxtLink>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Rest of the projects -->
        <div class="col-lg-4" v-for="item in rest" :key="item.id">
          <div class="item mt-50">
            <div class="img">
              <NuxtLink :to="`/project/${item.id}`">
                <img :src="item.image" alt="" class="radius-5" />
              </NuxtLink>
            </div>
            <div class="cont mt-30 d-flex align-items-center">
              <div>
                <span class="tag">{{ item.category }}</span>
                <h6 class="line-height-1">
                  <NuxtLink :to="`/project/${item.id}`">{{ item.title }}</NuxtLink>
                </h6>
              </div>
              <div class="ml-auto">
                <div class="arrow">
                  <NuxtLink :to="`/project/${item.id}`">
                    <svg class="arrow-right" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 34.2 32.3">
                      <line x1="0" y1="16" x2="33" y2="16"></line>
                      <line x1="17.3" y1="0.7" x2="33.2" y2="16.5"></line>
                      <line x1="17.3" y1="31.6" x2="33.5" y2="15.4"></line>
                    </svg>
                  </NuxtLink>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tech-preview {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.tech-tag {
  font-size: 12px;
  padding: 4px 8px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 4px;
  color: rgba(255, 255, 255, 0.7);
}

.item .img {
  overflow: hidden;
  border-radius: 5px;
}

.item .img img {
  transition: transform 0.3s ease;
}

.item:hover .img img {
  transform: scale(1.05);
}
</style>

<script setup>
import data from "@/data/portfolio.json";

const topTwo = data.slice(0, 2);
const rest = data.slice(2);
</script>
