<template>
  <h1 v-color="['blue', 'red', 'green']">Vue Custom Directive</h1>
</template>

<script setup>
function vColor(el, binding) {
  const colors = binding.value
  let i = 0
  setInterval(() => {
    el.style.color = colors[i]
    i++
    if (i === colors.length - 1) {
      i = 0
    }
  }, 500)
}
</script>
