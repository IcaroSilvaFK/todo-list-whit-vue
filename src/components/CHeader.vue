<script setup lang="ts">
defineEmits(['create-todo', 'change-text'])
defineProps({
  todo: {
    type: String,
    required: true
    // validator(value) {
    //   console.log(value)
    //   return true
    // }
  }
})
</script>
<template>
  <header>
    <div>
      <h1>TODO</h1>
    </div>
    <form @:submit.prevent="$emit('create-todo')">
      <input
        placeholder="Create new todo"
        :value="todo"
        @input="$emit('change-text', ($event.target as HTMLInputElement).value)"
      />
      <button>create</button>
    </form>
  </header>
</template>
<style lang="scss" scoped>
header {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  margin-top: 22px;
  width: 100%;

  div {
    display: flex;
    align-items: flex-start;
    width: 20%;
  }

  form {
    width: 20%;
    display: flex;
    justify-content: center;
    gap: 12px;

    input {
      width: 100%;
      padding: 6px;
      border-radius: 4px;
      border: 0;
      font-size: 1rem;
    }

    button {
      padding: 12px 18px;
      background: #805ad5;
      color: #f7fafc;
      border: 0;
      border-radius: 4px;

      &:hover {
        cursor: pointer;
        background: darken(#805ad5, 10%);
      }
    }
  }
}
</style>
