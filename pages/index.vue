<template>
  <div class="Home">
    <div class="note-wrapper">
      <Note
        :noteInfo="note"
        v-for="note in noteItems"
        :key="note.id"
        contenteditable
        @updateNote="onUpdateNote"
      />
    </div>
  </div>
</template>

<script>
import "./style.scss";
export default {
  data() {
    return {
      noteItems: [
        {
          id: 1,
          name: "test",
        },
        {
          id: 2,
          name: "test",
        },
        {
          id: 3,
          name: "test",
        },
        {
          id: 4,
          name: "test",
        },
        {
          id: 5,
          name: "test",
        },
        {
          id: 6,
          name: "test",
        },
        {
          id: 7,
          name: "test",
        },
        {
          id: 8,
          name: "test",
        },
        {
          id: 9,
          name: "test",
        },
        {
          id: 10,
          name: "test",
        },
        {
          id: 11,
          name: "test",
        },
        {
          id: 12,
          name: "test",
        },
      ],
    };
  },
  mounted(){
    this.init();
  },
  methods: {
    onUpdateNote(item) {
      const noteIndex = this.noteItems.findIndex((note) => note.id === item.id);
      if (noteIndex > -1) {
        this.noteItems[noteIndex].name = item.name;
        localStorage.setItem("notes", JSON.stringify(this.noteItems));
      }
    },
    init(){
      const listNoteString = localStorage.getItem("notes");
      if(listNoteString){
        const listNoteToArray = JSON.parse(listNoteString)
        this.noteItems = listNoteToArray
      }
    }
  },
};
</script>
