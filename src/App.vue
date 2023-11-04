<template>
  <h1 v-purple>Vue Custom Directive</h1>
</template>

<script setup>
function vPurple(el) {
  el.style.color = 'purple'
}
</script>
