<script>
import singleNote from './singleNote.vue'
import notesCount from './notesCount.vue'

export default {
  props: ['notes'],

  emits: ['localNotes'],

  components: { singleNote, notesCount },

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
      <notesCount :count="notes.length" />
    </div>
    <div class="notes" id="notes-container">
      <singleNote
        v-for="(note, idx) of notes"
        :key="idx"
        :note="note"
        :idx="idx"
        @removeNote="removeNote($event)"
        @updateNote="updateNote($event, idx)"
      />
    </div>
  </div>
</template>
