<template>
  <div class="main-container">
    <div class="container">
      <div v-for="note in list" v-bind:key="note.id" class="notes-container">
        <div class="notes" id="notes">
          <h4>{{ note.title }}</h4>
          <p>{{ note.description }}</p>
          <div class="note-icons" id="note-icons">
            <Icons :cardId="note.id" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import service from "../Services/User";
import Icons from "./Icons.vue";

export default {
  components: {
    Icons,
  },
  data() {
    return {
      list: {},
    };
  },
  mounted() {
    service.userNotesInArchive().then((response) => {
      console.log(response);
      this.list = response.data;
    });
  },
  methods: {},
};
</script>

<style lang="sass" scoped>
@import '../Styles/Archive.scss'
</style>
