<template>
  <main>
    <div class="container">
      <IceCreamSelection v-for="flavor in flavors" :key="flavor.flavor" :flavor="flavor" />
    </div>
  </main>
</template>

<script setup>
import IceCreamSelection from '../components/icecreamselection.vue'

const flavors = [
  { flavor: 'Vanilla', image: 'vanilla.png' },
  { flavor: 'Chocolate', image: 'chocolate.png' },
  { flavor: 'Strawberry', image: 'strawberry.png' },
  { flavor: "Cookies 'N Cream", image: 'oreo.png' },
  { flavor: 'Mint Chocolate', image: 'mint.png' },
  { flavor: 'Neapolitan', image: 'mixed.png' },
  { flavor: 'Coffee', image: 'coffee.png' },
  { flavor: 'Pistachio', image: 'pistachio.png' },
]
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 20px;
  gap: 15px;
}
</style>
