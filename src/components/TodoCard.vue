<script setup lang="ts">
import { TrashIcon } from '@heroicons/vue/24/solid'
defineEmits(['delete-todo'])
defineProps(['todo', 'id'])
</script>
<template>
  <li>
    <span>
      {{ todo }}
    </span>
    <button @click="$emit('delete-todo', id)">
      <TrashIcon />
    </button>
  </li>
</template>
<style lang="scss" scoped>
li {
  background: #4a5568;
  padding: 8px 16px;
  border-radius: 4px;

  display: flex;
  justify-content: space-between;
  align-items: center;
  span {
    max-width: 250px;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 1;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  button {
    background: transparent;
    border: 0;
    cursor: pointer;
    color: #e53e3e;

    svg {
      width: 20px;
      height: 20px;
    }

    &:hover {
      color: darken(#e53e3e, 10%);
    }
  }
}
</style>
