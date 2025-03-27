<script>
import NoteEditor from './NoteEditor.vue'

export default {
  props: ['modelValue'],

  emits: ['update:model-value'],

  components: { NoteEditor },

  methods: {
    notesWithUpdated(updated) {
      return this.modelValue.map(n => (n.id === updated.id ? updated : n))
    },
    notesWithRemoved(removed) {
      return this.modelValue.filter(n => n.id !== removed.id)
    },
  },
}
</script>

<template>
  <div class="notes" id="notes-container">
    <NoteEditor
      v-for="note of modelValue"
      :key="note.id"
      :note
      @note-removed="$emit('update:model-value', notesWithRemoved($event))"
      @note-updated="$emit('update:model-value', notesWithUpdated($event))"
    />
  </div>
</template>
