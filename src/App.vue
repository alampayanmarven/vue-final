<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">ParkingLot</RouterLink>
        <RouterLink to="/motorcycle">MotorCycle</RouterLink>
        <RouterLink to="/car">Car</RouterLink>
      </nav>

  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {

  font-size: 1.5rem;
  width: 100%;
  /* font-size: 12px; */
  text-align: center;
  margin-top: 2rem;
  margin-left: 38vw;
  display: flex;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  color: white;
  background-color: rgba(255, 64, 129, 0.6);
}

nav a {
  display: inline-block;
  padding: 0.5rem 1rem;
  border-left: 1px solid var(--color-border);
  color: white;
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    /* display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2); */
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
