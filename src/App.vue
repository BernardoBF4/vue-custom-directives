<template>
  <h1 v-if="show" v-color:slow.underline.italic="colors">Vue Custom Directive</h1>
  <!-- <h1 v-color:crazy="colors">Vue Custom Directive</h1> -->
  <button @click="show = !show">Toggle</button>
</template>

<script setup>
import { ref } from 'vue'
const colors = ref(['blue', 'red', 'green'])
const show = ref(true)

const vColor = {
  mounted(el, binding) {
    if (binding.modifiers.underline) {
      el.style.textDecoration = 'underline'
    }

    if (binding.modifiers.italic) {
      el.style.fontStyle = 'italic'
    }
    const speeds = {
      slow: 2000,
      normal: 1000,
      fast: 500,
      crazy: 100,
    }
    let i = 0
    el.__ColorInterval__ = setInterval(() => {
      console.log('Color is changing')
      el.style.color = binding.value[i]
      i++
      if (i === binding.value.length) {
        i = 0
      }
    }, speeds[binding.arg || 'normal'])
  },
  unmounted(el) {
    clearInterval(el.__ColorInterval__)
  },
}

setTimeout(() => {
  colors.value.push('pink')
}, 5000)
</script>
