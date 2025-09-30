<script setup>
import { reactive, onMounted } from 'vue';

// Animation state tracking
const showCards = reactive({
  left: false,
  rightExpanded: false,
  leftSecond: false,
  rightSecondExpanded: false
});

// Click handlers for GitHub navigation
const openTemplateRepo = () => {
  window.open('https://github.com/a-rossman0825/fullstack-template', '_blank');
};

const openKeeprRepo = () => {
  window.open('https://github.com/a-rossman0825/keepr', '_blank');
};

// Trigger entrance animations on mount
onMounted(() => {
  // Both left cards slide in together
  setTimeout(() => {
    showCards.left = true;
    showCards.leftSecond = true;
  }, 100);

  // Both right cards expand together (after left cards)
  setTimeout(() => {
    showCards.rightExpanded = true;
    showCards.rightSecondExpanded = true;
  }, 600);
});
</script>

<template>
  <section class="masonry-bg d-flex justify-content-center">
    <div class="masonry-container">
      <!-- Left Card: Project Image and Title -->
      <div class="project-card left-card" :class="{
        'enter': !showCards.left,
        'enter-active': showCards.left,
        'from-left': true
      }" @click="openTemplateRepo">
        <div class="project-image">
          <img src="@/assets/img/template-img.png" alt="Vue.js Fullstack Project Template" />
        </div>
        <div class="project-title">
          <h2>Vue.js Fullstack Project Template</h2>
        </div>
      </div>

      <!-- Right Card: Project Description -->
      <div class="project-card right-card" :class="{
        'card-collapsed': !showCards.rightExpanded,
        'card-expanded': showCards.rightExpanded
      }" @click="openTemplateRepo">
        <div class="project-description">
          <h3>Project Overview</h3>
          <div class="description-content">
            <p>
              This open source Vue.js fullstack project template provides a comprehensive and easy to use foundation for
              building modern web
              applications.
              It utilizes a Vue.js Frontend with full TypeScript Support for type-safe client-side development, and a
              .NET Backend with a C#/EFCore API supported by a SQL Database.
            </p>
            <p>
              Features include component-based design, reactive state management, SPA site routing, and modern build
              tooling
              with Vite and EF Core. The template is designed to accelerate development while maintaining best practices
              for code
              organization
              and maintainability.
            </p>
            <div class="tech-stack">
              <h4>Tech Stack:</h4>
              <ul>
                <li>Vue 3 & TypeScript</li>
                <li>Vite Build Tool</li>
                <li>SCSS Styling</li>
                <li>ESLint Configuration</li>
                <li>C#/EFCore Server with MySQL Database</li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <!-- Second Row: Keepr Project -->
      <!-- Left Card: Keepr Image and Title -->
      <div class="project-card left-card second-row" :class="{
        'enter': !showCards.leftSecond,
        'enter-active': showCards.leftSecond,
        'from-left': true
      }" @click="openKeeprRepo">
        <div class="project-image">
          <img src="@/assets/img/keepr-screenshots/Screenshot-1.png" alt="Keepr (Fullstack Pinterest Clone)" />
        </div>
        <div class="project-title">
          <h2>Keepr (Fullstack Pinterest Clone)</h2>
        </div>
      </div>

      <!-- Right Card: Keepr Description -->
      <div class="project-card right-card second-row" :class="{
        'card-collapsed': !showCards.rightSecondExpanded,
        'card-expanded': showCards.rightSecondExpanded
      }" @click="openKeeprRepo">
        <div class="project-description">
          <h3>Project Overview</h3>
          <div class="description-content">
            <p>
              Keepr is a full-stack Pinterest clone that allows users to create, organize, and share visual content
              through a modern web interface. Built with Vue.js frontend and a robust backend API, it provides seamless
              user experience for content discovery and curation.
            </p>
            <p>
              Features include user authentication, image upload and storage "Keeps" & "Vaults" creation and
              organization, social sharing capabilities, and responsive design. The application demonstrates full-stack
              development skills with modern web technologies.
            </p>
            <div class="tech-stack">
              <h4>Tech Stack:</h4>
              <ul>
                <li>Vue 3 & TypeScript Client</li>
                <li>SCSS Styling</li>
                <li>C# and MySQL Database</li>
                <li>JWT Authentication</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>


<style lang="scss" scoped>
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
  height: auto;
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  align-items: flex-start;
  padding: 40px 0;
}

/* Second row positioning */
.second-row {
  margin-top: 40px;
}

.project-card {
  background-color: var(--bs-primary);
  border-radius: 0.6rem;
  box-shadow: 2px 2px 3px rgb(47, 47, 47);
  color: #eaeaea;
  font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
  transition: box-shadow 400ms ease-in-out, transform 400ms ease-in-out;
  border: 1px solid transparent;

  &:hover {
    border: 1px solid rgba(135, 131, 131, 0.159);
    box-shadow: 3px 3px 4px var(--bs-primary);
    transform: translateY(-4px);
  }
}

/* Entrance animation states */
.project-card.enter {
  opacity: 0;
  transform-origin: center center;
}

.project-card.enter-active {
  opacity: 1;
  transition: opacity 500ms ease-in-out, transform 500ms ease-in-out;
  transform: translate(0, 0);
}

/* Directional entrance effects */
.project-card.from-left.enter {
  transform: translateX(-50px);
}

.project-card.from-left.enter-active {
  transform: translateX(0);
}

.project-card.from-top.enter {
  transform: translateY(-50px);
}

.project-card.from-top.enter-active {
  transform: translateY(0);
}

/* Ensure hover states work properly with animations */
.project-card.enter-active:hover {
  transform: translateY(-4px);
}

.left-card {
  flex: 0 0 45%;
  height: 350px;
  display: flex;
  flex-direction: column;
}

.right-card {
  flex: 0 0 50%;
  padding: 30px;
  overflow-y: auto;
  transition: height 800ms ease-in-out;
}

/* Separate hover transition for smooth effects */
.right-card:hover {
  transition: box-shadow 400ms ease-in-out, transform 400ms ease-in-out;
}

/* Card height states */
.right-card.card-collapsed {
  height: 120px;
  /* Just enough for the header */
}

.right-card.card-expanded {
  height: 350px;
  /* Full height to show all content */
  transition: height 800ms ease-in-out, box-shadow 400ms ease-in-out, transform 400ms ease-in-out;
}

/* Description content */
.right-card .description-content {
  margin-top: 20px;
  opacity: 0;
  transition: opacity 200ms ease-in-out 200ms;
  /* Delay opacity until height expands */
}

.right-card.card-expanded .description-content {
  opacity: 1;
}

.project-image {
  height: 250px;
  overflow: hidden;
  border-radius: 0.6rem 0.6rem 0 0;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

.project-title {
  flex: 1;
  padding: 20px 25px;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 0 0 0.6rem 0.6rem;
  display: flex;
  align-items: center;

  h2 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 600;
    color: #ffffff;
    text-align: center;
    width: 100%;
  }
}

.project-description {
  h3 {
    margin: 0 0 20px 0;
    font-size: 1.8rem;
    font-weight: 700;
    color: #ffffff;
    border-bottom: 2px solid rgba(255, 255, 255, 0.2);
    padding-bottom: 10px;
  }

  h4 {
    margin: 25px 0 15px 0;
    font-size: 1.3rem;
    font-weight: 600;
    color: #ffffff;
  }

  p {
    font-size: 1.1rem;
    line-height: 1.6;
    margin-bottom: 20px;
    color: #eaeaea;
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;

    li {
      background: rgba(255, 255, 255, 0.1);
      padding: 8px 15px;
      margin: 8px 0;
      border-radius: 4px;
      border-left: 3px solid var(--bs-warning);
      font-size: 1rem;

      &:hover {
        background: rgba(255, 255, 255, 0.15);
      }
    }
  }
}

/* Responsive design for smaller screens */
@media (max-width: 1030px) {
  .masonry-container {
    width: 100%;
    padding: 20px;
    flex-direction: column;
    height: auto;
    flex-wrap: nowrap;
  }

  .project-card {
    width: 100% !important;
    margin-bottom: 20px;
    height: auto !important;
  }

  .left-card {
    flex: none;
    height: auto !important;
    max-height: 400px;
  }

  .right-card {
    flex: none;
    height: auto !important;
    max-height: none !important;
    padding: 20px;
  }

  .right-card.card-collapsed,
  .right-card.card-expanded {
    height: auto !important;
  }

  .second-row {
    margin-top: 20px;
  }

  /* Stack order: template left, template right, keepr left, keepr right */
  .project-card:nth-child(1) {
    order: 1;
  }

  /* Vue template left */
  .project-card:nth-child(2) {
    order: 2;
  }

  /* Vue template right */
  .project-card:nth-child(3) {
    order: 3;
  }

  /* Keepr left */
  .project-card:nth-child(4) {
    order: 4;
  }

  /* Keepr right */

  .project-image {
    height: 200px;
  }

  .project-title {
    flex: none;
    padding: 15px 20px;
  }

  .project-description {
    h3 {
      font-size: 1.5rem;
      margin-bottom: 15px;
    }

    p {
      font-size: 1rem;
      line-height: 1.5;
      margin-bottom: 15px;
    }

    h4 {
      font-size: 1.2rem;
      margin: 20px 0 10px 0;
    }
  }
}
</style>