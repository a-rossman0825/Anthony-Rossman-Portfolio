<script setup>
import { AppState } from '@/AppState.js';
import { computed } from 'vue';


const techIcons = computed(() => AppState.techIcons);

</script>


<template>
  <section>
    <div class="">
      <h3 class="mb-3 mt-2">Technologies</h3>
    </div>

    <div  class="d-flex justify-content-center gap-4 tech-icons ms-4">
      <p v-for="techIcon in techIcons" :key="techIcon.name" :data-tooltip="techIcon.name" :aria-label="techIcon.name">
        <svg width="50" height="50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 128 128">
          <path v-for="(path, i) in techIcon.paths" :key="i" :d="path.d" :fill="path.fill || '#fff'" />
        </svg>   
      </p>  
    </div>
  </section>
</template>


<style lang="scss" scoped>

.tech-icons {
  flex-wrap: wrap;
}

h3 {
  font-size: 1.6em;
  font-weight: 600;
  letter-spacing: .05ch;
  padding-inline-start: 1rem;
}

p {
  position: relative; /* Essential for positioning the tooltip */
}

p::after {
  content: attr(data-tooltip); /* Get content from data-tooltip attribute */
  position: absolute;
  bottom: 105%; /* Position above the element */
  left: 50%;
  transform: translateX(-50%); /* Center the tooltip horizontally */
  background-color: #fff;
  color: #333;
  padding: 3px 8px;
  border-radius: 20px;
  white-space: nowrap; /* Prevent line breaks in the tooltip */
  opacity: 0; /* Initially hidden */
  visibility: hidden;
  transition: opacity 0.3s ease, visibility 0.3s ease; /* Smooth transition */
  z-index: 1000;
  font-size: 16px;
}

p:hover::after {
  opacity: 1;
  visibility: visible;
}
</style>