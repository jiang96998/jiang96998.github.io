---
layout: page
title: Gallery
permalink: /gallery/
nav: true
nav_order: 4
---

## Research Gallery

<div class="gallery">

  <div class="gallery-item">
    <img 
      src="{{ '/assets/img/gallery/1.jpg' | relative_url }}" 
      class="gallery-cover"
      onclick="openGallery('g1', 0)"
    >
    <h4>Robotic Ultrasound</h4>

    <!-- Modal -->
    <div id="g1" class="gallery-modal">
      <span class="close" onclick="closeGallery('g1')">&times;</span>

      <!-- arrows -->
      <span class="arrow left" onclick="changeSlide(-1)">❮</span>
      <span class="arrow right" onclick="changeSlide(1)">❯</span>

      <!-- images -->
      <img class="slide" src="{{ '/assets/img/gallery/1.jpg' | relative_url }}">
      <img class="slide" src="{{ '/assets/img/gallery/1.jpg' | relative_url }}">
      <img class="slide" src="{{ '/assets/img/gallery/1.jpg' | relative_url }}">
      <img class="slide" src="{{ '/assets/img/gallery/1.jpg' | relative_url }}">
    </div>
  </div>

</div>


<script>
let currentSlide = 0;
let slides = [];

function openGallery(id, index) {
  const modal = document.getElementById(id);
  modal.style.display = "block";

  slides = modal.querySelectorAll(".slide");
  currentSlide = index;

  showSlide(currentSlide);
}

function closeGallery(id) {
  document.getElementById(id).style.display = "none";
}

function showSlide(n) {
  slides.forEach(img => img.style.display = "none");
  slides[n].style.display = "block";
}

function changeSlide(step) {
  currentSlide += step;

  if (currentSlide >= slides.length) currentSlide = 0;
  if (currentSlide < 0) currentSlide = slides.length - 1;

  showSlide(currentSlide);
}
</script>