<template>
  <div class="products-section">
    <div class="products-page">
      <h2 class="page-title">Our Collection</h2>
      
      <div class="products-grid">
        <div v-for="product in products" :key="product.id" class="product-card">
          <div class="image-container">
            <img 
              :src="product.image" 
              :alt="product.name" 
              class="product-image"
              loading="lazy"
              @error="handleImageError"
            >
          </div>
          <div class="product-info">
            <h3>{{ product.name }}</h3>
            <p class="description">{{ product.description }}</p>
            <p class="price">₹{{ product.price.toFixed(2) }}</p>
            <button @click="addToCart(product)" class="add-to-cart-btn">
              Add to Cart
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import products from '../assets/products.json';

export default {
  data() {
    return {
      products: products.map(product => ({
        ...product,
        // Ensure image is properly resolved
        image: typeof product.image === 'string' ? require(`@/assets/images/${product.image.split('/').pop()}`) : product.image
      }))
    }
  },
  methods: {
    addToCart(product) {
      this.$router.push({
        path: '/cart',
        query: {
          id: product.id,
          name: product.name,
          price: product.price,
          image: product.image
        }
      });
    },
    handleImageError(event) {
      event.target.src = require('@/assets/images/D.jpeg');
      event.target.style.objectFit = 'contain';
    }
  }
}
</script>

<style scoped>
.products-section {
  background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 50%, #80deea 100%);
  min-height: 100vh;
  padding: 2rem 0;
}

.products-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.page-title {
  text-align: center;
  color: #006064;
  margin-bottom: 3rem;
  font-size: 2.5rem;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.product-card {
  background: rgba(255, 255, 255, 0.95);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
}

.image-container {
  width: 100%;
  height: 250px;
  overflow: hidden;
  position: relative;
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
  border-bottom: 1px solid #eee;
  position: absolute;
  top: 0;
  left: 0;
}

.product-info {
  padding: 1.5rem;
}

.product-info h3 {
  margin: 0 0 0.8rem 0;
  color: #2d3748;
  font-size: 1.3rem;
}

.description {
  color: #4a5568;
  margin-bottom: 1rem;
  font-size: 0.95rem;
  line-height: 1.5;
}

.price {
  font-weight: 700;
  color: #006064;
  margin: 1.2rem 0;
  font-size: 1.3rem;
}

.add-to-cart-btn {
  width: 100%;
  padding: 0.9rem;
  background: linear-gradient(to right, #006064, #00838F);
  color: white;
  border: none;
  border-radius: 25px;
  font-weight: 500;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 96, 100, 0.2);
}

.add-to-cart-btn:hover {
  background: #00838F;
}
</style>