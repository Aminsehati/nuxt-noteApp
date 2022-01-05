<template>
  <div class="Note">
    <div
      class="note-name"
      :contenteditable="contenteditable"
      @blur="updateTextNote($event, noteInfo.id)"
    >
      {{ noteInfo.name }}
    </div>
  </div>
</template>
<script>
import "./style.scss";
export default {
  props: {
    noteInfo: {
      type: Object,
      default: () => {},
    },
    contenteditable: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    updateTextNote(e, id) {
      const { textContent } = e.target;
      const textUpdateObject = {
        ...this.noteInfo,
        name: textContent,
      };
      this.$emit("updateNote", textUpdateObject);
    },
  },
};
</script>