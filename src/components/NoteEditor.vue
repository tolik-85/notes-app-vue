<script>
export default {
  props: ['note'],

  emits: ['note-removed', 'note-updated'],

  data() {
    return {
      localNote: { ...note },
    }
  },

  methods: {
    updateText(text) {
      this.$emit('note-updated', { ...this.localNote, text, isEditing: false })
    },
  },
}
</script>
<template>
  <div class="note-card">
    <div class="note-content">
      <p
        v-if="!localNote.isEditable"
        @dblclick="
          this.$emit('note-updated', { ...localNote, isEditable: true })
        "
      >
        {{ localNote.text }}
      </p>

      <textarea
        v-else
        :value="localNote.text"
        @blur="updateText($event.target.value)"
      >
      </textarea>
    </div>

    <div class="note-actions">
      <button @click="$emit('note-removed', note)">Удалить</button>
    </div>
  </div>
</template>
