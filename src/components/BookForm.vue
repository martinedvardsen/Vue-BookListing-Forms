<template>
  <form v-on:submit.prevent="bookSubmit(bookTitle, bookAuthor)" class="" action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
      <label for="finishedReading">Finished Reading</label>
      <input type="checkbox" v-model="bookData.finishedReading">
    </div>
    <div>
      <label for="borrowed">borrowed</label>
      <input v-model="bookData.ownership" type="radio" value="borrowed">
      <label for="bought">bought</label>
      <input v-model="bookData.ownership" type="radio" value="bought">
    </div>
    <button type="submit" name="button" v-on:submit.prevent="bookSubmit(bookData)">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>

<style>
</style>
