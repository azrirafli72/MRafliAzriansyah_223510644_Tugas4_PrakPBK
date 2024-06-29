<template>
  <div id="app" class="bg-gradient-to-r from-purple-400 via-pink-500 to-red-500 min-h-screen flex items-center justify-center p-8">
    <div class="container max-w-5xl mx-auto bg-white p-8 rounded-lg shadow-xl">
      <header class="text-center mb-12">
        <h1 class="text-5xl font-bold text-indigo-900 mb-4">📚 Perpustakaan Online</h1>
        <p class="text-lg text-gray-700">Aturlah Buku Anda di Sini</p>
      </header>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <div class="bg-indigo-50 p-6 rounded-lg shadow-md">
          <book-form @add-book="addBook" class="bg-indigo-50 p-6 rounded-lg shadow-md"></book-form>
        </div>
        <div class="bg-indigo-50 p-6 rounded-lg shadow-md">
          <book-list :books="books" @view-book="viewBook" @delete-book="deleteBook"></book-list>
        </div>
      </div>
      <div class="mt-12 bg-indigo-50 p-6 rounded-lg shadow-md">
        <book-detail :book="selectedBook"></book-detail>
      </div>
    </div>
  </div>
</template>

<script>
import BookForm from './components/BookForm.vue';
import BookList from './components/BookList.vue';
import BookDetail from './components/BookDetail.vue';

export default {
  name: 'App',
  components: {
    BookForm,
    BookList,
    BookDetail
  },
  data() {
    return {
      books: [],
      selectedBook: null
    }
  },
  mounted() {
    // Load books from localStorage
    const storedBooks = localStorage.getItem('books');
    if (storedBooks) {
      this.books = JSON.parse(storedBooks);
    }
  },
  methods: {
    addBook(newBook) {
      this.books.push(newBook);
      // Save books to localStorage
      localStorage.setItem('books', JSON.stringify(this.books));
    },
    viewBook(book) {
      this.selectedBook = book;
    },
    deleteBook(bookId) {
      this.books = this.books.filter(book => book.id !== bookId);
      // Save books to localStorage
      localStorage.setItem('books', JSON.stringify(this.books));
      if (this.selectedBook && this.selectedBook.id === bookId) {
        this.selectedBook = null;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 40px;
  background-color: #f0f0f0;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  overflow-y: auto; /* Tambahkan overflow-y untuk scroll vertikal jika perlu */
}

header {
  margin-bottom: 30px;
}

h1 {
  color: #333;
}

p {
  color: #555;
}

.grid {
  gap: 20px;
}

.bg-indigo-50 {
  background-color: #e2e8f0;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  overflow: hidden; /* Hindari konten yang terlalu panjang keluar dari kotak */
}

.space-y-4 > *:not([hidden]) ~ *:not([hidden]) {
  /* Style the direct children of the space-y-4 element */
  margin-top: 1rem;
}

.w-full {
  width: 100%;
}

.bg-green-500 {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

.bg-green-600 {
  background-color: #45a049;
}

.text-white {
  color: white;
}

.font-bold {
  font-weight: bold;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.hover:bg-green-600 {
  transition: background-color 0.3s ease;
}

.transition {
  transition: all 0.3s ease;
}

.duration-200 {
  transition-duration: 200ms;
}

.text-gray-700 {
  color: #333;
}

.border {
  border: 1px solid #ccc;
}

.border-gray-300 {
  border-color: #ddd;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.p-2 {
  padding: 0.5rem;
}

.focus:border-blue-500 {
  border-color: #2196F3;
}

.focus:outline-none {
  outline: none;
}

.focus:ring-2 {
  box-shadow: 0 0 0 2px #2196F3;
}

.focus:ring-blue-200 {
  box-shadow: 0 0 0 2px #90CAF9;
}

.text-indigo-600 {
  color: #4299E1;
}

.hover:underline {
  text-decoration: none;
  transition: text-decoration 0.3s ease;
}

.hover:underline:hover {
  text-decoration: underline;
}

.text-red-600 {
  color: #F44336;
}

.flex {
  display: flex;
}

.justify-between {
  justify-content: space-between;
}

.items-center {
  align-items: center;
}

.py-4 {
  padding-top: 1rem;
  padding-bottom: 1rem;
}

.divide-y {
  border-top: 1px solid #ddd;
}

.divide-gray-200 {
  border-color: #ddd;
}

.space-x-2 > *:not([hidden]) ~ *:not([hidden]) {
  /* Style the direct children of the space-x-2 element */
  margin-left: 0.5rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-semibold {
  font-weight: 600;
}

.mb-6 {
  margin-bottom: 1.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.text-gray-800 {
  color: #222;
}

.strong {
  font-weight: bold;
}


</style>