<template>
  <section class="book-filter-container">
    <header class="filter-header">
      <h1>{{ title }}</h1>
    </header>
    
    <div class="filter-content">
      <label for="searchInput" class="filter-label">Filtro:</label>
      <input 
        type="text" 
        id="searchInput" 
        v-model="searchTerm" 
        class="filter-input"
        placeholder="Pesquisar livros..."
      >
      
      <ul class="book-list">
        <li 
          v-for="book in filteredBooks" 
          :key="book.id" 
          class="book-item"
        >
          {{ book.id }}. {{ book.title }} - {{ book.author }}
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';

const title = ref('Busca de Livros');
const searchTerm = ref('');

const books = ref([
  { id: 1, title: 'O Pequeno Príncipe', author: 'Antoine de Saint-Exupéry' },
  { id: 2, title: 'Dom Casmurro', author: 'Machado de Assis' },
  { id: 3, title: 'A Metamorfose', author: 'Franz Kafka' },
  { id: 4, title: '1984', author: 'George Orwell' },
  { id: 5, title: 'Cem Anos de Solidão', author: 'Gabriel García Márquez' },
  { id: 6, title: 'Orgulho e Preconceito', author: 'Jane Austen' }
]);

const filteredBooks = computed(() => {
  return books.value.filter(book => 
    book.title.toLowerCase().includes(searchTerm.value.toLowerCase()) ||
    book.author.toLowerCase().includes(searchTerm.value.toLowerCase())
  );
});
</script>

<style scoped>
.book-filter-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  background-color: #f5f5f5;
  border-radius: 8px;
}

.filter-header {
  text-align: center;
  margin-bottom: 1.5rem;
}

.filter-header h1 {
  color: #2c3e50;
  font-size: 1.8rem;
}

.filter-content {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.filter-label {
  font-weight: bold;
  color: #333;
}

.filter-input {
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

.book-list {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

.book-item {
  padding: 0.8rem;
  margin-bottom: 0.5rem;
  background-color: #42b983;
  color: white;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.book-item:hover {
  background-color: #369f6b;
}
</style>