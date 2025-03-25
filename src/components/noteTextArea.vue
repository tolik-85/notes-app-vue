<script>
export default {
  props: ['note'],
  emits: ['updatedNote'],

  data() {
    return {
      textAreaValue: this.note,
    }
  },
  methods: {
    updateNote() {
      this.$emit('updatedNote', this.textAreaValue)
    },
  },
  watch: {
    // textAreaValue: {
    //   handler() {
    //     console.log(this.textAreaValue)
    //   },
    // },
  },
}
</script>
<template>
  <textarea v-model.trim="textAreaValue" @blur="updateNote"></textarea>
</template>
