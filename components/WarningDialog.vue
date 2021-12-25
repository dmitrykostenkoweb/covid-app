<template>
  <div class="dialog__wrapper">
    <slot></slot>
  </div>
</template>

<script>
export default {}
</script>

<style>
.dialog__wrapper {
  position: fixed;
  bottom: 10%;
  right: 10%;
  left: 10%;
  padding: 16px;
  border: 1px solid red;
  border-radius: 4px;
  background-color: black;
  box-shadow: 10px 10px 10px black;
}
</style>
