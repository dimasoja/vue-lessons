<template>
  <div class="wrapper">
  <div class="wrapper-content">
    <section>
      <div class="container">
     <h1> {{ title }} </h1>
  <message v-if="message" :message="message" />
    <div class="message" v-if="message" >
      <p>{{ message }}</p>
    </div>
    <!-- new note -->
    <newNote :note="note" @addNote="addNote" />
    <notes  :notes="notes" />
    <!-- note list -->
   
    </div>
    </section>
  </div>
  </div>
  </div>
</template>

<script>

import message from '@/components/Message.vue'
import newNote from '@/components/NewNote.vue'
import notes from '@/components/Notes.vue'



export default {
  components: {
    message: message, newNote, notes
    
  },
  data(){
    return { 
      title: 'Notes App',
      message: 'hello',
      note: {
        title: '',
        descr: ''
      },
      notes: [
        {
          title: 'First Note',
          descr: 'Description for first note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Second Note',
          descr: 'Description for second note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Third Note',
          descr: 'Description for third note',
          date: new Date(Date.now()).toLocaleString()
        }
      ]

    }
    
  },
   methods: {
    addNote () {
      // console.log(this.note)
      let {title, descr} = this.note

      if (title === '') {
        this.message = 'title can`t be blank!'
        return false
      }

      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleString()
      })
      this.message = null
      this.note.title = ''
      this.note.descr = ''
    }
  }
}
</script>
 
<style lang="scss">

</style>
