<template>
  <div>
    <div id="appContainer">
      <speech
        :addNote="addNote"
        :deleteNote="deleteNote"
        :removeAllNotes="removeAllNotes"
      ></speech>

      <transition-group name="fade" tag="div">
        <noteItem 
        v-for="note in notes" 
        :key="note.id" 
        :noteItem="note"
        >
      </noteItem>
      </transition-group>
    </div>
  </div>
</template>

<script>
import noteItem from '../components/STT/noteItem'
import speech from '../components/STT/speech.vue';

export default {
  name: "SttView",
  components: {
    noteItem,
    speech,
  },

  data() {
    return {
      notes:[ ]
    };
  },
  methods: {
addNote(note) {
  this.notes.push({
    id: this.notes.length + 1,
    note: note,
  });
},


    deleteNote(id){
      this.notes.splice(
        this.notes.findIndex(n => n.id == id),
      1
      );
    },
    removeAllNotes(){
      this.notes = []
    }
  },
};
</script>

<style scoped>
/* Fade animasyonu */
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s ease;
}
.fade-enter, 
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
