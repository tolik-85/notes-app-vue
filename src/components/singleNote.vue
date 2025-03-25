<script>
import noteTextArea from './noteTextArea.vue'

export default {
  components: { noteTextArea },

  props: ['note', 'idx'],

  emits: ['removeNote', 'updateNote'],

  data() {
    return {
      isEditing: false,
    }
  },

  methods: {
    removeNote() {
      this.$emit('removeNote', this.idx)
    },
    onDbClickHandler(e) {
      this.isEditing = true
    },
    updateNote(newNote) {
      this.$emit('updateNote', newNote)
      this.isEditing = false
    },
  },
  watch: {
    // note: {
    //   handler(newNote) {
    //     console.log(newNote)
    //   },
    // },
  },
}
</script>
<template>
  <div class="note-card">
    <div class="note-content">
      <p v-if="!isEditing" @dblclick="onDbClickHandler">{{ note }}</p>
      <noteTextArea
        v-else
        :note="note"
        :idx="idx"
        @updatedNote="updateNote($event)"
      />
    </div>
    <div class="note-actions">
      <button @click="removeNote">Удалить</button>
    </div>
  </div>
</template>
