<template>
    <div v-if="book" style="background-color: azure; padding: 30px; border-radius: 25px;">
      <h3 class="text-2xl font-semibold text-indigo-600 mb-6">Book Detail</h3>
      <br />
      <p style="text-align: left"><strong>Title    :</strong> {{ book.title }}</p>
      <p style="text-align: left;"><strong>Author :</strong> {{ book.author }}</p>
      <p style="text-align: justify;"><strong>Description:</strong> {{ book.description }}</p>
      <p style="text-align: justify;"><strong>Content:</strong> {{ book.content }}</p>
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