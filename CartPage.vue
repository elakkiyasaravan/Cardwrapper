<template>
  <div class="cart-section">
    <div class="cart-page fade-in">
      <h2 class="page-title slide-in-left">Your Cart</h2>
      
      <div v-if="cartItems.length === 0" class="empty-cart">
        <p>Your cart is empty</p>
        <router-link to="/products" class="shop-btn hover-scale">
          Continue Shopping
        </router-link>
      </div>
      
      <div v-else>
        <div class="cart-items">
          <div v-for="item in cartItems" :key="item.id" class="cart-item hover-scale">
            <img :src="item.image" :alt="item.name" class="item-image" loading="lazy">
            <div class="item-details">
              <h3>{{ item.name }}</h3>
              <p>₹{{ item.price.toFixed(2) }}</p>
            </div>
          </div>
        </div>
        
        <button @click="proceedToPayment" class="payment-btn hover-scale">
          Proceed to Payment
        </button>
        
        <div v-if="showConfirmation" class="confirmation-message fade-in">
          <svg class="checkmark" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 52 52">
            <circle class="checkmark__circle" cx="26" cy="26" r="25" fill="none"/>
            <path class="checkmark__check" fill="none" d="M14.1 27.2l7.1 7.2 16.7-16.8"/>
          </svg>
          <h3>Order Confirmed!</h3>
          <p>Your order has been placed successfully.</p>
          <router-link to="/products" class="shop-btn hover-scale">
            Back to Shopping
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cartItems: [],
      showConfirmation: false
    }
  },
  created() {
    if (this.$route.query.id) {
      this.cartItems.push({
        id: this.$route.query.id,
        name: this.$route.query.name,
        price: parseFloat(this.$route.query.price),
        image: this.$route.query.image
      });
    }
  },
  methods: {
    proceedToPayment() {
      this.showConfirmation = true;
      setTimeout(() => {
        this.cartItems = [];
      }, 500);
    }
  }
}
</script>

<style scoped>
.cart-section {
  background: linear-gradient(135deg, #fff8e1 0%, #ffecb3 100%);
  min-height: 100vh;
  padding: 2rem 0;
}

.cart-page {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 15px;
  box-shadow: 0 8px 32px rgba(31, 38, 135, 0.1);
}

.page-title {
  text-align: center;
  color: #6C63FF;
  margin-bottom: 2rem;
  font-size: 2.2rem;
}

.empty-cart {
  text-align: center;
  padding: 3rem;
  animation: fadeIn 0.6s ease-out;
}

.empty-cart p {
  margin-bottom: 1.5rem;
  font-size: 1.2rem;
}

.shop-btn {
  display: inline-block;
  background: #6C63FF;
  color: white;
  padding: 0.8rem 1.8rem;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 500;
  box-shadow: 0 4px 15px rgba(108, 99, 255, 0.2);
}

.cart-items {
  margin-bottom: 2rem;
}

.cart-item {
  display: flex;
  gap: 1.5rem;
  align-items: center;
  padding: 1.2rem;
  background: white;
  border-radius: 12px;
  margin-bottom: 1rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
}

.item-image {
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.item-details h3 {
  margin: 0 0 0.5rem 0;
  color: #2d3748;
}

.item-details p {
  font-weight: 600;
  color: #6C63FF;
  font-size: 1.1rem;
}

.payment-btn {
  width: 100%;
  padding: 1rem;
  background: linear-gradient(to right, #4CAF50, #8BC34A);
  color: white;
  border: none;
  border-radius: 25px;
  font-size: 1.1rem;
  font-weight: 500;
  cursor: pointer;
  margin-top: 1rem;
  box-shadow: 0 4px 15px rgba(76, 175, 80, 0.3);
  transition: all 0.3s ease;
}

.confirmation-message {
  margin-top: 2rem;
  padding: 2rem;
  background: #e8f5e9;
  color: #2e7d32;
  border-radius: 12px;
  text-align: center;
  animation: fadeIn 0.6s ease-out;
}

.checkmark {
  width: 80px;
  height: 80px;
  margin-bottom: 1rem;
}

.checkmark__circle {
  stroke-dasharray: 166;
  stroke-dashoffset: 166;
  stroke-width: 2;
  stroke-miterlimit: 10;
  stroke: #4CAF50;
  fill: none;
  animation: stroke 0.6s cubic-bezier(0.65, 0, 0.45, 1) forwards;
}

.checkmark__check {
  transform-origin: 50% 50%;
  stroke-dasharray: 48;
  stroke-dashoffset: 48;
  stroke: #4CAF50;
  stroke-width: 3;
  stroke-miterlimit: 10;
  animation: stroke 0.3s cubic-bezier(0.65, 0, 0.45, 1) 0.6s forwards;
}

@keyframes stroke {
  100% {
    stroke-dashoffset: 0;
  }
}
</style>