<template>
  <nav class="navbar navbar-expand-lg static">
    <div class="container">
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="icon-bar"><i class="fas fa-bars"></i></span>
      </button>
      <div class="collapse navbar-collapse justify-content-center" id="navbarSupportedContent">
        <ul class="navbar-nav">
          <li class="nav-item">
            <NuxtLink class="nav-link" to="/">
              <span class="rolling-text">Home</span>
            </NuxtLink>
          </li>

          <li class="nav-item">
            <a class="nav-link" href="#about-me" data-scroll-nav="0" @click="scrollToSection">
              <span class="rolling-text">About</span>
            </a>
          </li>

          <li class="nav-item">
            <a
              class="nav-link"
              href="#my-portfolio"
              data-scroll-nav="3"
              @click="scrollToSection"
            >
              <span class="rolling-text">Portfolio</span>
            </a>
          </li>

          <li class="nav-item">
            <a class="nav-link" href="#my-blog" data-scroll-nav="5" @click="scrollToSection">
              <span class="rolling-text">Blog</span>
            </a>
          </li>

          <li class="nav-item">
            <a
              class="nav-link"
              href="#my-certificates"
              data-scroll-nav="2"
              @click="scrollToSection"
            >
              <span class="rolling-text">Certificates</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { onMounted, onUnmounted } from "vue";

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});

function handleScroll() {
  let navbar = document.querySelector(".navbar");
  if (window.scrollY > 350) navbar.classList.add("nav-scroll");
  else navbar.classList.remove("nav-scroll");
}

function scrollToSection(event) {
  if (!event.currentTarget.getAttribute("data-scroll-nav")) return;

  event.preventDefault();
  let sectionIndex = event.currentTarget.getAttribute("data-scroll-nav");
  let section = document.querySelector(`[data-scroll-index="${sectionIndex}"]`);

  if (section) {
    setTimeout(() => {
      section.scrollIntoView();
    }, 500);
  }
}

onMounted(() => {
  let elements = document.querySelectorAll(".rolling-text");

  elements.forEach((element) => {
    let innerText = element.innerText;
    element.innerHTML = "";

    let textContainer = document.createElement("div");
    textContainer.classList.add("block");

    for (let letter of innerText) {
      let span = document.createElement("span");
      span.innerText = letter.trim() === "" ? "\xa0" : letter;
      span.classList.add("letter");
      textContainer.appendChild(span);
    }

    element.appendChild(textContainer);
    element.appendChild(textContainer.cloneNode(true));
  });

  elements.forEach((element) => {
    element.addEventListener("mouseover", () => {
      element.classList.remove("play");
    });
  });
});
</script>
