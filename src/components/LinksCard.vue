<script setup>
import { AppState } from '@/AppState.js';
import { computed } from 'vue';

const linkIcons = computed(() => AppState.linkIcons);
</script>


<template>
  <section>
    <div class="d-flex justify-content-center mt-4 pt-3 ms-2 gap-4 link-icons">
      <a v-for="link in linkIcons" :key="link.name" :href="link.url" target="_blank" rel="noopener noreferrer"
        :aria-label="link.name" class="link-svg-wrapper">
        <svg width="50" height="50" xmlns="http://www.w3.org/2000/svg" :viewBox="String(link.viewBox || '0 0 128 128')">
          <path v-for="(path, i) in link.paths" :key="i" :d="path.d" :fill="path.fill || '#fff'"
            :transform="path.transform ?? undefined" />
        </svg>
      </a>
    </div>
  </section>
</template>


<style lang="scss" scoped>
.link-icons {
  flex-wrap: wrap;
}

.link-svg-wrapper {
  position: relative;
  display: inline-block;
  transition: transform 0.2s;
}

.link-svg-wrapper:hover {
  transform: scale(1.08);
}
</style>