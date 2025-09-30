<script setup>
import { AppState } from '@/AppState.js';
import { computed, reactive, onMounted } from 'vue';

const cards = computed(() => AppState.cards);

const showMap = reactive({});


AppState.cards.forEach(card => {
  showMap[card.id] = false;
});

const directions = computed(() => AppState.animationDirs);

onMounted(() => {
  animateCardEntrance([6, 1, 2, 3, 5, 4, 7]);
});

function animateCardEntrance(cardSequence) {
  const delay = 140;
  cardSequence.forEach((id, idx) => {
    setTimeout(() => {
      showMap[id] = true;
    }, idx * delay + 50);
  })
};

</script>

<template>
  <div class="masonry-bg d-flex justify-content-center">
    <div class="masonry-container">
      <div v-for="card in cards" :key="`home-page-card-${card.id}`" class="masonry-card" :data-id="card.id" :class="[
        { center: card.center },
        card.darkBG ? 'card-bg-dark' : 'card-bg-blue',
        directions[card.id],
        showMap[card.id] ? 'enter-active' : 'enter'
      ]" :style="{
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
  height: 1100px;
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
  transition: box-shadow 400ms ease-in-out, transform 400ms ease-in-out;
  cursor: pointer;
  border: 1px solid transparent;

  &:hover {
    border: 1px solid rgba(135, 131, 131, 0.159);
    box-shadow: 3px 3px 4px var(--bs-primary);
    transform: translate(0, -4px);
  }
}

.masonry-card.enter-active:hover {
  transform: translate(0, -4px);
}

.masonry-card.enter {
  opacity: 0;
  transform-origin: center center;
}

.masonry-card.enter-active {
  opacity: 1;

  transition: box-shadow 400ms ease-in-out, opacity 400ms ease-in-out, transform 400ms ease-in-out;
  transform: translate(0, 0);
}

.masonry-card.from-left.enter {
  transform: translateX(-28px);
}

.masonry-card.from-right.enter {
  transform: translateX(28px);
}

.masonry-card.from-top.enter {
  transform: translateY(-28px);
}

.masonry-card.from-bottom.enter {
  transform: translateY(28px);
}

.masonry-card.fade.enter {
  transform: translateY(6px);
}

.masonry-card.center.enter {
  opacity: 0;
  transform: translate(-50%, 0);
}

.masonry-card.center.enter-active {
  opacity: 1;
  transform: translate(-50%, 0);
  transition: box-shadow 400ms ease-in-out, opacity 400ms ease-in-out, transform 400ms ease-in-out;
  will-change: opacity, transform;
  backface-visibility: hidden;
}

.masonry-card.center {
  font-size: 2rem;
  font-weight: 700;
  transform: translate(-50%, 0);
  transition: box-shadow 400ms ease-in-out, transform 400ms ease-in-out;
  will-change: transform;
  cursor: pointer;
  border: 1px solid transparent;

  &:hover {
    border: 1px solid rgba(135, 131, 131, 0.159);
    box-shadow: 3px 3px 4px var(--bs-primary);
    transform: translate(-50%, -4px);
  }
}

.masonry-card.center.enter-active:hover {
  transform: translate(-50%, -4px);
}

.name-card {
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 1px;
}


@media (max-width: 1030px) {
  .masonry-container {
    position: static;
    width: 100%;
    height: auto;
    padding: 20px;
    display: flex;
    flex-direction: column;
  }

  .masonry-card {
    position: relative !important;
    left: auto !important;
    top: auto !important;
    width: 100% !important;
    transform: none !important;
    margin: 10px 0;
    height: auto !important;
    min-height: auto !important;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;
    text-align: center;
  }

  .masonry-card[data-id="2"] {
    display: none !important;
  }

  .masonry-card[data-id="6"] {
    order: 1;
  }

  .masonry-card[data-id="3"] {
    order: 2;
  }

  .masonry-card[data-id="1"] {
    order: 3;
  }

  .masonry-card[data-id="4"] {
    order: 4;
  }

  .masonry-card[data-id="7"] {
    order: 5;
  }

  .masonry-card[data-id="5"] {
    order: 6;
  }
}
</style>
