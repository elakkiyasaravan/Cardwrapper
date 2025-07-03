<!--<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
<template>
  <div id="app">
    <Header />
    <transition name="fade" mode="out-in">
      <router-view />
    </transition>
  </div>
</template>

<script>
import Header from './components/Header.vue';
export default { components: { Header } };
</script>

<style>
.fade-enter-active, .fade-leave-active { transition: opacity 0.4s ease; }
.fade-enter-from, .fade-leave-to { opacity: 0; }
</style>-->
<template>
  <div>
    <nav class="navbar navbar-expand-lg">
      <div class="container-fluid">
        <a class="navbar-brand" href="/">Vue E-Commerce</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <div class="navbar-nav me-auto">
            <router-link to="/" class="nav-link">Home</router-link>
            <router-link to="/products" class="nav-link">Products</router-link>
            <router-link to="/cart" class="nav-link">
              Cart <span class="badge bg-light text-dark rounded-pill">{{ cartItems.length }}</span>
            </router-link>
          </div>
        </div>
      </div>
    </nav>
    <div class="container mt-4">
      <router-view />
    </div>
  </div>
</template>

<script>
import { eventBus } from './eventBus';

export default {
  data() {
    return {
      cartItems: [],
    };
  },
  created() {
    eventBus.on('add-to-cart', (product) => {
      const existingItem = this.cartItems.find((item) => item.id === product.id);
      if (existingItem) {
        existingItem.quantity = (existingItem.quantity || 1) + 1;
      } else {
        this.cartItems.push({ ...product, quantity: 1 });
      }
    });
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Playfair+Display:wght@400;500;600&display=swap');

body {
  font-family: 'Montserrat', sans-serif;
  background-color: #f8f9fa;
}

.navbar {
  background: linear-gradient(45deg, #6a11cb, #2575fc);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.navbar-brand,
.nav-link {
  color: white !important;
  font-weight: 600;
  font-family: 'Playfair Display', serif;
}

.nav-link:hover {
  color: rgba(255, 255, 255, 0.8) !important;
}

.badge {
  font-size: 0.7rem;
  vertical-align: middle;
}
</style>