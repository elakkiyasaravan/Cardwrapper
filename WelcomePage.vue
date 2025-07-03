<template>
  <div class="welcome-section">
    <div class="welcome-container">
      <div class="hero-content">
        <h1 class="hero-title animate__animated animate__fadeInDown">Elegance Redefined</h1>
        <p class="hero-subtitle animate__animated animate__fadeIn animate__delay-1s">
          Discover our exquisite collection of premium dresses
        </p>
        <router-link 
          to="/products" 
          class="hero-button animate__animated animate__fadeInUp animate__delay-1s"
        >
          Explore Collection
        </router-link>
      </div>
    </div>
  </div>
</template>

<style scoped>
.welcome-section {
  /* 4-shade elegant gradient */
  background: linear-gradient(
    135deg,
    #f8e3ff 0%,       /* Soft lilac */
    #e2c2ff 25%,      /* Light purple */
    #d1a4ff 50%,      /* Medium purple */
    #b388e8 100%      /* Deep lavender */
  );
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  color: #3a284b;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: background 1.5s ease;
}

.welcome-section:hover {
  background: linear-gradient(
    135deg,
    #f8e3ff 0%,
    #e2c2ff 30%,
    #d1a4ff 70%,
    #b388e8 100%
  );
}

.welcome-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: url('https://images.unsplash.com/photo-1539109136881-3be0616acf4b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80') center/cover;
  opacity: 0.08;
  z-index: 1;
  transition: opacity 0.5s ease;
}

.welcome-container:hover::before {
  opacity: 0.12;
}

.hero-content {
  position: relative;
  z-index: 2;
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  backdrop-filter: blur(2px);
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  text-shadow: 0 2px 8px rgba(255, 255, 255, 0.3);
  letter-spacing: 0.5px;
  transition: all 0.4s ease;
}

.hero-subtitle {
  font-size: 1.5rem;
  margin-bottom: 2.5rem;
  opacity: 0.9;
  font-weight: 400;
  letter-spacing: 0.3px;
  transition: all 0.4s ease 0.1s;
}

.hero-button {
  display: inline-block;
  background: linear-gradient(to right, #7b4397, #dc2430);
  color: white;
  padding: 1.2rem 3rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.1rem;
  transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
  box-shadow: 0 4px 15px rgba(123, 67, 151, 0.3);
  border: none;
  position: relative;
  overflow: hidden;
}

.hero-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.2),
    transparent
  );
  transition: 0.5s;
}

.hero-button:hover {
  transform: translateY(-5px) scale(1.02);
  box-shadow: 0 8px 25px rgba(123, 67, 151, 0.4);
}

.hero-button:hover::before {
  left: 100%;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-subtitle {
    font-size: 1.2rem;
  }
  
  .hero-button {
    padding: 1rem 2rem;
    font-size: 1rem;
  }
}

/* Animation imports */
@import url('https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css');
</style>