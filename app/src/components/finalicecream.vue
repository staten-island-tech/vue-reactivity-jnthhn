// FinalIceCream.vue
<template>
  <div class="final-card">
    <h2>Your Ice Cream Creation</h2>
    <div class="ice-cream-details" v-if="cone || flavor || toppings.length">
      <div v-if="cone" class="detail-item">
        <h3>Cone:</h3>
        <p>{{ cone.type }}</p>
        <img :src="cone.image" :alt="cone.type" />
      </div>
      <div v-if="flavor" class="detail-item">
        <h3>Flavor:</h3>
        <p>{{ flavor.flavor }}</p>
        <img :src="flavor.image" :alt="flavor.flavor" />
      </div>
      <div v-if="toppings.length" class="detail-item">
        <h3>Toppings:</h3>
        <div class="toppings-grid">
          <div v-for="topping in toppings" :key="topping.name" class="topping">
            <p>{{ topping.name }}</p>
            <img :src="topping.image" :alt="topping.name" />
          </div>
        </div>
      </div>
      <button @click="$emit('reset')" class="reset-button">Start Over</button>
    </div>
    <div v-else class="empty-state">
      <p>Start building your ice cream by selecting a cone, flavor, and toppings!</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  cone: Object,
  flavor: Object,
  toppings: {
    type: Array,
    default: () => [],
  },
})
</script>

<style scoped>
.final-card {
  width: 300px;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  background-color: #fff;
  position: fixed;
  right: 20px;
  top: 50px;
}

.ice-cream-details {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.detail-item {
  text-align: center;
}

.detail-item img {
  max-width: 100px;
  border-radius: 8px;
}

.toppings-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
}

.topping {
  text-align: center;
}

.topping img {
  max-width: 50px;
  border-radius: 4px;
}

.reset-button {
  width: 100%;
  padding: 10px;
  margin-top: 20px;
  background-color: #ff6b6b;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 250ms;
}

.reset-button:hover {
  background-color: #ff5252;
}

.empty-state {
  text-align: center;
  color: #666;
}
</style>
