---
layout: page
permalink: /photos/
title: Photos
# description: Photography portfolio and travel memories
nav: true
nav_order: 4
---

<!-- ## Photography Portfolio -->

<div class="gallery-grid">
  <!-- Add your photos here -->
  <!-- Example structure for each photo:
  <div class="gallery-item">
    <img src="/assets/img/photos/your-photo.jpg" alt="Description">
    <div class="gallery-caption">
      <h3>Title</h3>
      <p>Description and location</p>
    </div>
  </div>
  -->
  <div class="gallery-item">
    <img src="/assets/img/photos/latte_art_mania.jpg" alt="Latte art mania@Tokyo">
    <div class="gallery-caption">
      <h3>Latte Art Mania</h3>
      <p>東京都港区北青山2-9-13</p>
    </div>
  </div>
  
  <div class="gallery-item">
    <img src="/assets/img/photos/corgi.jpg" alt="CUHK Campus">
    <div class="gallery-caption">
      <h3>Corgi</h3>
      <!-- <p>The Chinese University of Hong Kong</p> -->
    </div>
  </div>
  

<!-- ## Travel Memories

<div class="gallery-grid">
  <!-- Add your travel photos here -->
<!-- </div> -->

<style>
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  padding: 20px 0;
}

.gallery-item {
  position: relative;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  aspect-ratio: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.gallery-item:hover img {
  transform: scale(1.05);
}

.gallery-caption {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0,0,0,0.7);
  color: white;
  padding: 10px;
  transform: translateY(100%);
  transition: transform 0.3s ease;
}

.gallery-item:hover .gallery-caption {
  transform: translateY(0);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .gallery-grid {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  }
}

@media (max-width: 480px) {
  .gallery-grid {
    grid-template-columns: 1fr;
  }
}
</style> 