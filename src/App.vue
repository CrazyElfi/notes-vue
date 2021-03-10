<template>
  <div class="wrapper">

    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>
          <message v-if="message" :message="message"/>

          <!--        new note-->
          <div class="new-note">
            <input type="text"
                   v-model="note.title">
            <textarea v-model="note.desc"></textarea>
            <button @click="addNode">
              New note
            </button>
          </div>
          <!--        note list-->
          <div class="notes">
            <div class="note"
                 v-for="(note,index) in notes"
                 :key="index">
              <div class="note-header">
                <p>{{ note.title }}</p>
              </div>
              <div class="note-body">
                <p>{{ note.desc }}</p>
                <span>{{ note.date }}</span>
              </div>
            </div>
          </div>

        </div>
      </section>
    </div>
    <!--    <div id="app">-->
    <!--      <h2>hello</h2>-->
    <!--      <img alt="Vue logo" src="./assets/logo.png">-->
    <!--    </div>-->

  </div>
</template>

<script>
import message from "@/components/Message.vue";

export default {
  components: {
    message
  },
  data () {
    return {
      title: 'Notes App',
      message: null,
      note: {
        title: '',
        desc: '',
      },
      notes: [
        {
          title: "First Note",
          desc: "Description for first note",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "Second Note",
          desc: "Description for second note",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "Third Note",
          desc: "Description for third note",
          date: new Date(Date.now()).toLocaleString(),
        },
      ]
    }
  },
  methods: {
    addNode() {
      let {title, desc} = this.note;

      if (title === "") {
        this.message = "Title can't be empty!";
        return false
      }
      this.notes.push({
        title,
        desc,
        date: new Date(Date.now()).toLocaleString(),
      })
      this.message = null;
      this.note.title = '';
      this.note.desc = '';
    }
  }
}
</script>

<style>

</style>
