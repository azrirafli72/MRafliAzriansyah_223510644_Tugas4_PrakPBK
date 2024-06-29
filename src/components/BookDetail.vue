<template>
    <div v-if="book">
      <h3 class="text-2xl font-semibold text-indigo-600 mb-4">Book Detail</h3>
      <p><strong>Title:</strong> {{ book.title }}</p>
      <p><strong>Author:</strong> {{ book.author }}</p>
      <p><strong>Description:</strong> {{ book.description }}</p>
      <p><strong>Content:</strong> {{ book.content }}</p>
    </div>
    <div v-else>
      <p class="text-gray-700">Pilih Buku untuk Dilihat Detailnya</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookDetail',
    props: ['book']
  }
  </script>