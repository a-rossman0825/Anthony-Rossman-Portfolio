<script setup>
import { useRoute } from 'vue-router';


const route = useRoute();

</script>


<template>
  <section class="container-fluid">
    <div class="row justify-content-center">
      <div class=" mt-4 justify-content-between rounded projects-btn-wrapper align-items-center d-flex">
        <RouterLink :to="{ name: 'Home' }" class="col-6">
          <div class="text-center rounded fw-bold"
            :class="route.name == 'Home' ? 'projects-btn-active' : 'projects-btn-inactive'">
            Home
          </div>
        </RouterLink>
        <RouterLink :to="{ name: 'Projects' }" class="col-6">
          <div class=" text-center rounded fw-bold"
            :class="route.name == 'Projects' ? 'projects-btn-active' : 'projects-btn-inactive'">
            Projects
          </div>
        </RouterLink>
      </div>
    </div>
  </section>
</template>


<style lang="scss" scoped>
a {
  text-decoration: none;
  color: var(--bs-secondary);
}

.projects-btn-wrapper {
  background-color: var(--bs-dark);
  margin-left: 15px;
  padding-left: 5px;
  padding-right: 5px;
  margin-right: 15px;
  cursor: pointer;
  width: 400px;
  box-sizing: border-box;
}

.projects-btn-active,
.projects-btn-inactive {
  flex: 1 1 0;
  min-width: 0;
  padding-top: 3px;
  margin-top: 5px;
  margin-bottom: 5px;
  padding-bottom: 3px;
  transition: background-color 0.3s, color 0.3s, box-shadow 0.3s;
}

.projects-btn-active {
  background-color: rgb(50, 51, 52);
  color: var(--bs-light);
}

.projects-btn-inactive {
  background-color: transparent;
  color: var(--bs-secondary);
  
  &:hover {
    color: rgb(86, 87, 88);
  }
}
</style>