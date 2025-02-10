<template>
  <main>
    <div class="container">
      <!-- Cone Selection -->
      <div class="selection-section" id="cone-selection">
        <h2>Choose your cone</h2>
        <div class="selection-grid">
          <ConeSelection
            v-for="cone in cones"
            :key="cone.type"
            :cone="cone"
            @select-cone="selectCone"
          />
        </div>
      </div>

      <!-- Ice Cream Selection -->
      <div class="selection-section" id="icecream-selection">
        <h2>Choose your flavor</h2>
        <div class="selection-grid">
          <IceCreamSelection
            v-for="flavor in flavors"
            :key="flavor.flavor"
            :flavor="flavor"
            @select-flavor="selectFlavor"
          />
        </div>
      </div>

      <!-- Toppings Selection -->
      <div class="selection-section" id="topping-selection">
        <h2>Choose your toppings</h2>
        <div class="selection-grid">
          <ToppingSelection
            v-for="topping in toppings"
            :key="topping.name"
            :topping="topping"
            @select-topping="selectTopping"
          />
        </div>
      </div>

      <!-- Final Ice Cream Creation -->
      <FinalIceCream
        :cone="selectedCone"
        :flavor="selectedFlavor"
        :toppings="selectedToppings"
        @reset="resetSelections"
      />
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue'
import IceCreamSelection from '../components/icecreamselection.vue'
import ConeSelection from '../components/coneselection.vue'
import ToppingSelection from '../components/toppingselection.vue'
import FinalIceCream from '../components/finalicecream.vue'

const cones = [
  { type: 'Waffle Cone', image: 'waffle-cone.png' },
  { type: 'Sugar Cone', image: 'sugar-cone.png' },
  { type: 'Cake Cone', image: 'cake-cone.png' },
  { type: 'Chocolate Cone', image: 'chocolate-cone.png' },
]

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

const toppings = [
  { name: 'Sprinkles', image: 'sprinkles.png' },
  { name: 'Hot Fudge', image: 'hot-fudge.png' },
  { name: 'Caramel', image: 'caramel.png' },
  { name: 'Whipped Cream', image: 'whipped-cream.png' },
  { name: 'Cherry', image: 'cherry.png' },
  { name: 'Nuts', image: 'nuts.png' },
  { name: 'M&Ms', image: 'm&ms.png' },
  { name: 'Chocolate Chips', image: 'chocolate-chips.png' },
]

const selectedCone = ref(null)
const selectedFlavor = ref(null)
const selectedToppings = ref([])

const selectCone = (cone) => {
  selectedCone.value = cone
}

const selectFlavor = (flavor) => {
  selectedFlavor.value = flavor
}

const selectTopping = (topping) => {
  const index = selectedToppings.value.findIndex((t) => t.name === topping.name)
  if (index === -1) {
    selectedToppings.value.push(topping)
  } else {
    selectedToppings.value.splice(index, 1)
  }
}

const resetSelections = () => {
  selectedCone.value = null
  selectedFlavor.value = null
  selectedToppings.value = []
}
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Creates three equal columns */
  gap: 20px;
  padding: 20px;
}

.selection-section {
  margin-bottom: 40px;
}

.selection-section h2 {
  margin-bottom: 20px;
  text-align: center;
}

.selection-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px;
}

#cone-selection {
  grid-column: 1;
}

#icecream-selection {
  grid-column: 2;
}

#topping-selection {
  grid-column: 3;
}
</style>
