<script setup>
function handleClickedOutside() {
  alert('You clicked outside')
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
