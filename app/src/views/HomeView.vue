<template>
  <main>
    <div>
      <IceCreamSelection v-for="flavor in flavors" :key="flavor.flavor" :flavor="flavor" />
    </div>
  </main>
</template>

<script setup>
import IceCreamSelection from '../components/icecreamselection.vue'

const flavors = [
  { flavor: 'vanilla', image: 'vanilla.png' },
  { flavor: 'chocolate', image: '' },
  { flavor: 'strawberry', image: '' },
  { flavor: 'oreo', image: '' },
  { flavor: 'mint chocolate chip', image: '' },
]
</script>

<style scoped></style>
