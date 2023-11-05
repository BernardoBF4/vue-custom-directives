<template>
  <h1 v-color:slow="colors">Vue Custom Directive</h1>
  <h1 v-color:crazy="colors">Vue Custom Directive</h1>
</template>

<script setup>
import { ref } from 'vue'
const colors = ref(['blue', 'red', 'green'])

function vColor(el, binding) {
  const speeds = {
    slow: 2000,
    normal: 1000,
    fast: 500,
    crazy: 100,
  }
  let i = 0
  setInterval(() => {
    el.style.color = binding.value[i]
    i++
    if (i === binding.value.length) {
      i = 0
    }
  }, speeds[binding.arg || 'normal'])
}

setTimeout(() => {
  colors.value.push('pink')
}, 5000)
</script>
