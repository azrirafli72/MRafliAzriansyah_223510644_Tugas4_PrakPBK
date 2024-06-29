<template>
    <div>
      <form @submit.prevent="addBook" class="space-y-4">
        <div>
          <label for="title" class="block text-gray-700 font-bold mb-2">Title:</label>
          <input v-model="title" id="title" required class="border border-gray-300 rounded-lg p-2 w-full focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-200">
        </div>
        <div>
          <label for="author" class="block text-gray-700 font-bold mb-2">Author:</label>
          <input v-model="author" id="author" required class="border border-gray-300 rounded-lg p-2 w-full focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-200">
        </div>
        <div>
          <label for="content" class="block text-gray-700 font-bold mb-2">Content:</label>
          <textarea v-model="content" id="content" required class="border border-gray-300 rounded-lg p-2 w-full focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-200"></textarea>
        </div>
        <div>
          <label for="description" class="block text-gray-700 font-bold mb-2">Description:</label>
          <textarea v-model="description" id="description" required class="border border-gray-300 rounded-lg p-2 w-full focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-200"></textarea>
        </div>
        <button type="submit" class="w-full bg-green-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-green-600 transition duration-200">Save</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookForm',
    data() {
      return {
        title: '',
        author: '',
        content: '',
        description: ''
      }
    },
    methods: {
      addBook() {
        this.$emit('add-book', {
          id: Date.now(),
          title: this.title,
          author: this.author,
          content: this.content,
          description: this.description
        });
        this.title = '';
        this.author = '';
        this.content = '';
        this.description = '';
      }
    }
  }
  </script>