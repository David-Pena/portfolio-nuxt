<script setup lang="ts">
import type { Project } from "types/project";
import portfolioData from "@/data/portfolio.json";

interface Props {
  project: Project;
}

const props = defineProps<Props>();

// Get current project index and calculate next/prev
const currentIndex = computed(() => portfolioData.findIndex((p) => p.id === props.project.id));
const prevProject = computed(() =>
  currentIndex.value > 0 ? portfolioData[currentIndex.value - 1] : null
);
const nextProject = computed(() =>
  currentIndex.value < portfolioData.length - 1 ? portfolioData[currentIndex.value + 1] : null
);

function getTechIcon(tech: string): string {
  const iconMap: Record<string, string> = {
    "Vue.js": "fab fa-vuejs",
    "Node.js": "fab fa-node-js",
    TailwindCSS: "fab fa-css3",
  };

  return iconMap[tech] || "fas fa-code";
}
</script>

<template>
  <section class="project section-padding">
    <div class="container">
      <!-- Project Header Image -->
      <div class="row justify-content-center mb-80">
        <div class="col-lg-11">
          <div class="img-container">
            <img :src="project.image" :alt="project.title" class="project-main-img" />
            <div v-if="project.isWip" class="wip-badge">Work in Progress</div>
          </div>
        </div>
      </div>

      <div class="row justify-content-center">
        <div class="col-lg-11">
          <div class="row justify-content-center">
            <div class="col-lg-7">
              <div class="cont md-mb50">
                <h3 class="mb-15 fw-500">{{ project.title }}</h3>
                <p>{{ project.brief }}</p>

                <!-- Tech Stack Section -->
                <div class="tech-stack-container mt-40">
                  <h6 class="sub-title mb-20">Technologies Used</h6>
                  <div class="tech-pills">
                    <div v-for="tech in project.techStack" :key="tech" class="tech-pill">
                      <span class="tech-icon">
                        <i :class="getTechIcon(tech)"></i>
                      </span>
                      {{ tech }}
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-lg-4" style="position: relative">
              <div class="info" id="sticky_item" style="position: sticky; top: 0px">
                <ul>
                  <li class="mb-30">
                    <span class="sub-title"
                      ><i class="far fa-calendar-alt mr-10"></i> Date :</span
                    >
                    <p>{{ project.date }}</p>
                  </li>
                  <li class="mb-30">
                    <span class="sub-title"
                      ><i class="fas fa-list-ul mr-10"></i> Categories :</span
                    >
                    <p>{{ project.category }}</p>
                  </li>
                  <li class="mb-30">
                    <span class="sub-title"><i class="far fa-user mr-10"></i> Client :</span>
                    <p>{{ project.client }}</p>
                  </li>
                  <li>
                    <span class="sub-title"><i class="fas fa-globe mr-10"></i> Website :</span>
                    <a :href="project.website" target="_blank">{{ project.website }}</a>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="next-prev">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-lg-11">
            <div class="d-flex align-items-center mt-80 pt-80 bord-thin-top">
              <div class="prev" v-if="prevProject">
                <h6 class="sub-title">
                  <NuxtLink :to="`/project/${prevProject.id}`">
                    <i class="fas fa-long-arrow-alt-left"></i> {{ prevProject.title }}
                  </NuxtLink>
                </h6>
              </div>
              <div class="next ml-auto" v-if="nextProject">
                <h6 class="sub-title">
                  <NuxtLink :to="`/project/${nextProject.id}`">
                    {{ nextProject.title }} <i class="fas fa-long-arrow-alt-right"></i>
                  </NuxtLink>
                </h6>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tech-stack-container {
  background: rgba(255, 255, 255, 0.02);
  border-radius: 12px;
  padding: 25px;
  border: 1px solid rgba(255, 255, 255, 0.05);
}

.tech-pills {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

.tech-pill {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0.01));
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  font-size: 14px;
  transition: all 0.3s ease;
}

.tech-pill:hover {
  transform: translateY(-2px);
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.02));
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.tech-icon {
  font-size: 16px;
  opacity: 0.8;
}

.next-prev .sub-title a {
  color: #fff;
  font-size: 15px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s;
}

.next-prev .sub-title a:hover {
  color: #75dab4;
  text-decoration: none;
}

.next-prev i {
  margin: 0 10px;
  font-size: 14px;
}

.img-container {
  position: relative;
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.05);
}

.project-main-img {
  width: 100%;
  height: auto;
  border-radius: 12px;
  transition: transform 0.5s ease;
}

.img-container:hover .project-main-img {
  transform: scale(1.02);
}

.wip-badge {
  position: absolute;
  top: 20px;
  right: 20px;
  background: rgba(117, 218, 180, 0.9);
  color: #000;
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 500;
  backdrop-filter: blur(4px);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.mb-80 {
  margin-bottom: 80px;
}
</style>
