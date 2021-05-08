<template>
    <li>
        {{ todo.text }}
        <button @click="$emit('remove', todo)">
            X
        </button>
    </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      done: false 
    }
  }
}
</script>