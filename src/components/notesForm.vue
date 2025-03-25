<script>
export default {
  emits: ['newNote'],
  data() {
    return {
      noteValue: '',
    }
  },
  methods: {
    emitNote() {
      this.$emit('newNote', this.noteValue)
      this.noteValue = ''
    },
  },
  watch: {
    // noteValue(newValue) {
    //   console.log(newValue)
    // },
  },
}
</script>
<template>
  <div class="section">
    <div class="note-form">
      <textarea
        @keyup.enter="emitNote"
        v-model.trim="noteValue"
        id="note-content"
        rows="4"
        placeholder="Введите вашу заметку..."
      ></textarea>
      <button id="add-note" @click="emitNote">Добавить заметку</button>
    </div>
  </div>
</template>
