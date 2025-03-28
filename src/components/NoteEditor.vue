<script>
export default {
  props: ['note'],

  emits: ['note-removed', 'note-updated'],

  data() {
    return {
      localNote: { ...this.note },
    }
  },

  watch: {
    note: {
      deep: true,
      handler(newValue) {
        this.localNote = { ...newValue }
      },
    },

    localNote: {
      deep: true,
      handler(newValue, oldValue) {
        if (newValue === oldValue) {
          this.$emit('note-updated', { ...newValue })
        }
      },
    },
  },
}
</script>

<template>
  <div class="note-card">
    <div class="note-content">
      <p v-if="!localNote.isEditable" @dblclick="localNote.isEditable = true">
        {{ localNote.text }}
      </p>

      <textarea
        v-else
        :value="localNote.text"
        @blur="localNote.isEditable = false"
        @change="localNote.text = $event.target.value"
      >
      </textarea>
    </div>

    <div class="note-actions">
      <button @click="$emit('note-removed', { ...localNote })">Удалить</button>
    </div>

    <div
      @click="
        $emit('note-updated', {
          id: localNote.id,
          text: '55555',
          isEditable: true,
        })
      "
    >
      X
    </div>
  </div>
</template>
