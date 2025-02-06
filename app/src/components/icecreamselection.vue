<script setup>
defineProps({
  flavor: Object,
})
</script>

<template>
  <div>
    <h2>{{ flavor.flavor }}</h2>
    <img :src="flavor.image" alt="" />
  </div>
</template>

<style scoped></style>
