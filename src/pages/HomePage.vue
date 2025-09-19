<script setup>
import { AppState } from '@/AppState.js';
import { computed } from 'vue';

const cards = computed(() => AppState.cards);

</script>

<template>
  <div class="masonry-bg d-flex justify-content-center">
    <div class="masonry-container">
      <div v-for="card in cards" :key="`home-page-card-${card.id}`" class="masonry-card" :class="[{ center: card.center }, card.darkBG ? 'card-bg-dark' : 'card-bg-blue'] " :style="{
        left: card.left,
        top: card.top,
        width: card.width,
        height: card.height,
      }">
        <component :is="card.component" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.masonry-bg {
  position: relative;
  min-height: 700px;
  width: 100vw;
  background: #000000;
  overflow: hidden;
}

.masonry-container {
  position: relative;
  width: 1030px;
  height: 1000px;
}
.card-bg-dark {
  background-color: var(--bs-dark);
}

.card-bg-blue {
  background-color: var(--bs-primary);
}

.masonry-card {
  position: absolute;
  border-radius: .6rem;
  box-shadow: 2px 2px 3px rgb(47, 47, 47);
  display: flex;
  
  font-size: 1.2rem;
  color: #eaeaea;
  font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
  transition: box-shadow 0.3s ease-in-out, transform 0.3s ease-in-out;
  cursor: pointer;
  border: 1px solid transparent;

  &:hover {
  border: 1px solid rgba(135, 131, 131, 0.159);
  box-shadow: 3px 3px 4px var(--bs-primary);
  transform: translate(0, -4px);
  }
}

.masonry-card.center {
  font-size: 2rem;
  font-weight: 700;
  transform: translate(-50%, 0);
  transition: box-shadow 0.3s ease-in-out, transform 0.3s ease-in-out;
  cursor: pointer;
  border: 1px solid transparent;
  
  &:hover {
    border: 1px solid rgba(135, 131, 131, 0.159);
    box-shadow: 3px 3px 4px var(--bs-primary);
    transform: translate(-50%, -4px);
  }
}

.name-card {
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 1px;
}
</style>
