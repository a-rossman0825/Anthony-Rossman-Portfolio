<script setup>
import DescCard from '@/components/DescCard.vue';
import NameCard from '@/components/NameCard.vue';
import PfpCard from '@/components/PfpCard.vue';
import TitleCard from '@/components/TitleCard.vue';



const cards = [
  {
    id: 1,
    left: '2%',
    top: '22%',
    width: '643px',
    height: '180px',
    darkBG: true,
    component: DescCard,
  },
  {
    id: 2,
    left: '66%',
    top: '22%',
    width: '300px',
    height: '375px',
    darkBG: true,
    component: PfpCard,
  },
  {
    id: 3,
    left: '2%',
    top: '50%',
    width: '330px',
    height: '160px',
    darkBG: false,
    component: TitleCard,
  },
  // {
  //   id: 4,
  //   left: '15%',
  //   top: '100%',
  //   width: '170px',
  //   height: '200px',
  //   darkBG: true,
  //   component: CardJobTitle,
  // },
  // {
  //   id: 5,
  //   left: '45%',
  //   top: '100%',
  //   width: '260px',
  //   height: '140px',
  //   darkBG: true,
  //   component: CardJobTitle,
  // },
  // {
  //   id: 6,
  //   left: '75%',
  //   top: '100%',
  //   width: '180px',
  //   height: '200px',
  //   darkBG: true,
  //   component: CardJobTitle,
  // },
  {
    id: 7,
    left: '50%',
    top: '50%',
    width: '300px',
    height: '330px',
    component: NameCard,
    darkBG: true,
    center: true
  }
];
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
  height: 700px;
}
.card-bg-dark {
  background-color: #191a1c;
}

.card-bg-blue {
  background-color: rgb(10, 63, 91);
}

.masonry-card {
  position: absolute;
  border-radius: .6rem;
  box-shadow: 2px 2px 3px rgb(47, 47, 47);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  color: #eaeaea;
  font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
  transition: box-shadow 0.2s, transform 0.2s;
  cursor: pointer;
  border: 1px solid transparent;

  &:hover {
  border: 1px solid rgba(135, 131, 131, 0.159);
  box-shadow: 3px 3px 4px rgba(100, 99, 99, 0.576);
  transform: translate(0, -4px);
  }
}

.masonry-card.center {
  font-size: 2rem;
  font-weight: 700;
  transform: translate(-50%, 0);
  transition: box-shadow 0.2s, transform 0.2s;
  cursor: pointer;
  border: 1px solid transparent;
  
  &:hover {
    border: 1px solid rgba(135, 131, 131, 0.159);
    box-shadow: 3px 3px 4px rgba(100, 99, 99, 0.576);
    transform: translate(-50%, -4px);
  }
}

.name-card {
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 1px;
}
</style>
