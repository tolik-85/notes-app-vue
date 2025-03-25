<script>
export default {
  props: ['notes'],
}
</script>

<template>
  <span class="notes-count">Всего заметок: {{ notes.length }}</span>
</template>
