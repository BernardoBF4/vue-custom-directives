<template>
  <h1 v-color="colors">Vue Custom Directive</h1>
</template>

<script setup>
import { ref } from 'vue'
const colors = ref(['blue', 'red', 'green'])

function vColor(el, binding) {
  let i = 0
  setInterval(() => {
    el.style.color = binding.value[i]
    i++
    if (i === binding.value.length) {
      i = 0
    }
  }, 1000)
}

setTimeout(() => {
  colors.value.push('pink')
}, 5000)
</script>
