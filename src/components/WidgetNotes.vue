<script>
import NoteSubmitter from './NoteSubmitter.vue'
import NotesList from './NotesList.vue'
import NotesCount from './notesCount.vue'

export default {
  components: { NoteSubmitter, NotesList, NotesCount },

  data() {
    return {
      notes: [],
    }
  },
}
</script>

<template>
  <div class="container">
    <div class="section">
      <h1 @click="notes[0].text = '!!!!!!!'">Приложение для заметок</h1>
      <h1
        @click="
          notes[0] = {
            id: 999999,
            text: '999999',
            isEditable: true,
          }
        "
      >
        Приложение для заметок
      </h1>
    </div>

    {{ notes }}

    <NoteSubmitter @note-submitted="notes.push($event)" />

    <div class="section">
      <div class="notes-header">
        <h2>Список заметок</h2>

        <NotesCount :notes />
      </div>

      <NotesList v-model="notes" />

      <br />
      <br />
      <br />
      <br />
      <br />

      <NotesList v-model="notes" />
    </div>
  </div>
</template>

<!-- <NotesBottom :model-value="notes" @update:model-value="notes = $event" /> -->

<style>
* {
  box-sizing: border-box;
}
body {
  font-family: Arial, sans-serif;
  background-color: #f8f8ff;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}
.container {
  margin: 0 auto;
  max-width: 1000px;
  min-width: 300px;
  width: 100%;
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
.section {
  margin-bottom: 20px;
  padding: 20px;
  background: #f4f4f9;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.05);
}
h1 {
  text-align: center;
  color: #333;
  margin-top: 0;
}
.note-form {
  display: flex;
  flex-direction: column;
}
.note-form textarea {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin-bottom: 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
}
.note-form button {
  padding: 10px;
  font-size: 16px;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.note-form button:hover {
  background-color: #0056b3;
}
.notes-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.notes-count {
  font-size: 16px;
  color: #555;
}
.notes {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
}
.note-card {
  background: #fff;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  position: relative;
}
.note-card p {
  margin: 0;
  color: #333;
}
.note-card .note-content {
  margin-bottom: 10px;
}
.note-card .note-actions {
  text-align: right;
}
.note-card button {
  background-color: #ff4d4d;
  border: none;
  color: white;
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}
.note-card button:hover {
  background-color: #cc0000;
}
</style>
