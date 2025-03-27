<script>
const makeId = () => Math.trunc(Math.random() * 0xffff_ffff)

const initNote = () => ({
  id: makeId(),
  text: '',
  isEditable: false,
})

export default {
  emits: ['note-submitted'],

  data() {
    return {
      note: initNote(),
    }
  },

  methods: {
    submitNote() {
      this.$emit('note-submitted', this.note)
      this.note = initNote()
    },
  },
}
</script>
<template>
  <div class="section">
    <div class="note-form">
      <textarea
        @keyup.enter="submitNote"
        v-model.trim="note.text"
        id="note-content"
        rows="4"
        placeholder="Введите вашу заметку..."
      ></textarea>
      <button id="add-note" @click="submitNote">Добавить заметку</button>
    </div>
  </div>
</template>
