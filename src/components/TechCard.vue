<script setup>
import { AppState } from '@/AppState.js';
import { computed } from 'vue';


const techIcons = computed(() => AppState.techIcons);

</script>


<template>
  <section>
    <div class="">
      <h3 class="mb-5 mt-4">Technologies</h3>
    </div>

    <div class="d-flex justify-content-center gap-5 tech-icons">
      <a v-for="techIcon in techIcons" :key="techIcon.name" :data-tooltip="techIcon.name" :href="techIcon.link" target="_blank">
        <svg width="50" height="50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 128 128">
          <path v-for="(path, i) in techIcon.paths" :key="i" :d="path.d" :fill="path.fill || '#fff'"
            :transform="path.transform ? path.transform.toString() : undefined" />
        </svg>
      </a>
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

a {
  text-decoration: none;
  position: relative;
  opacity: 90%;
}

svg {
  opacity: 80%;
  transition: all .4s ease-in-out;

  &:hover {
    opacity: 100%;
    filter: drop-shadow(0 2px 6px rgb(27, 134, 167));
    transform: scale(1.1);
  }
}

a::after {
  content: attr(data-tooltip);
  position: absolute;
  bottom: 105%;
  left: 50%;
  transform: translateX(-50%);
  background-color: var(--bs-primary);
  color: var(--bs-secondary);
  padding: 3px 8px;
  border-radius: 20px;
  white-space: nowrap;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.3s ease, visibility 0.3s ease;
  z-index: 1000;
  font-size: 16px;
}

a:hover::after {
  opacity: 1;
  visibility: visible;
}
</style>