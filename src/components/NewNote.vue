<template>
  <div class="new-note">
      <input v-model="note.title" type="text">
      <textarea v-model="note.descr"></textarea>
      <button class="btn btnPrimary" @click="addNote">New note</button>
  </div>
</template>

<script>

export default {
  props:  {
    note: {
      type: Object,
      require: true
    }
    
  },
  methods: {
    addNote () {
      this.$emit('addNote', this.note)
    }
  }
}
</script>
