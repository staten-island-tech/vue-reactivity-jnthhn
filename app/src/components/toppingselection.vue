<template>
  <div class="card" @click="handleClick">
    <h2>{{ topping.name }}</h2>
    <img :src="topping.image" :alt="topping.name" />
  </div>
</template>

<script setup>
const props = defineProps({
  topping: Object,
  onSelect: Function,
})

const handleClick = () => {
  if (props.onSelect) {
    props.onSelect(props.topping)
  }
}
</script>

<style scoped>
.card {
  width: 200px;
  padding: 15px;
  margin: 10px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  text-align: center;
  background-color: #fff;
  cursor: pointer;
  transition:
    transform 250ms,
    filter 250ms;
}
.card:hover {
  transform: scale(1.1);
  filter: brightness(90%);
}
.card img {
  width: 100%;
  border-radius: 8px;
}
.card h2 {
  font-size: 1.2rem;
  margin-bottom: 10px;
}
</style>
