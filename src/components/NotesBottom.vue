<script>
import NoteEditor from './NoteEditor.vue'
import NotesCount from './NotesCount.vue'

export default {
  props: ['notes'],

  emits: ['localNotes'],

  components: { NoteEditor, NotesCount },

  data() {
    return {}
  },

  methods: {
    removeNote(noteIdx) {
      const localNotes = [...this.notes]
      localNotes.splice(noteIdx, 1)
      this.$emit('localNotes', localNotes)
    },
    updateNote(newNote, idx) {
      const localNotes = [...this.notes]
      localNotes.splice(idx, 1, newNote)
      this.$emit('localNotes', localNotes)
    },
  },

  watch: {
    // notes: {
    //   deep: true,
    //   handler(newNotes) {
    //     console.log('newNotes', newNotes)
    //   },
    // },
  },
}
</script>
<template>
  <div class="section">
    <div class="notes-header">
      <h2>Список заметок</h2>
      <NotesCount :notes />
    </div>
    <div class="notes" id="notes-container">
      <NoteEditor
        v-for="note of notes"
        :key="note.id"
        :note
        @note-removed="removeNote($event)"
        @note-updated="updateNote($event, note)"
      />
    </div>
  </div>
</template>
