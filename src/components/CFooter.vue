<script setup lang="ts"></script>
<template>
  <footer>
    <slot name="footer"></slot>
  </footer>
</template>

<style scoped lang="scss">
footer {
  display: flex;
  align-items: center;
  justify-content: center;
  max-width: 40%;
  width: 100%;
  margin: 22px auto;
  font-style: italic;
  font-size: 0.625rem;
}
</style>
