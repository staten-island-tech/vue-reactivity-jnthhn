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
  { flavor: 'vanilla', image: 'vanilla.png' },
  { flavor: 'chocolate', image: 'chocolate.png' },
  { flavor: 'strawberry', image: 'strawberry.png' },
  { flavor: 'oreo', image: 'oreo.png' },
  { flavor: 'mint chocolate chip', image: 'mint.png' },
]
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 20px;
}
</style>
