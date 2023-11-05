<script setup>
function handleClickedOutside() {
  alert('You clicked outside')
}

const vClickOutside = {
  mounted(el, binding) {
    el.__ClickOutsideHandler__ = (event) => {
      if (!(el === event.target || el.contains(event.target))) {
        binding.value()
      }
    }
    document.body.addEventListener('click', el.__ClickOutsideHandler__)
  },
  unmounted(el) {
    document.body.removeEventListener('click', el.__ClickOutsideHandler__)
  },
}
</script>

<template>
  <h2>Click Outside</h2>
  <div class="box" v-click-outside="handleClickedOutside">Here is some text</div>
</template>

<style>
.box {
  border: 2px solid blue;
  height: 200px;
  width: 200px;
}
</style>
