<template>
    <div>
      <h3 class="text-2xl font-semibold text-indigo-600 mb-6">List Buku Tersedia</h3>
      <ul class="divide-y divide-gray-200">
        <li v-for="book in books" :key="book.id" class="flex justify-between items-center py-4">
          <div class="text-gray-800">
            <strong>{{ book.title }}</strong> by {{ book.author }}
          </div>
          <div class="flex space-x-2">
            <button @click="$emit('view-book', book)" class="text-indigo-600 hover:underline">View</button>
            <button @click="$emit('delete-book', book.id)" class="text-red-600 hover:underline">Delete</button>
          </div>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookList',
    props: ['books']
  }
  </script>