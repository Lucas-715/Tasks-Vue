<template>
  <section class="quote-wrapper">
    <div class="quote-content">
      <blockquote v-if="currentQuote">
        <p class="quote-text">"{{ currentQuote }}"</p>
        <cite class="quote-author">{{ currentAuthor }}</cite>
      </blockquote>
      <button 
        class="quote-button" 
        @click="generateQuote"
      >
        Gerar Nova Citação
      </button>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Citacao',
  data() {
    return {
      quotes: [
        { 
          quote: "A imaginação é mais importante que o conhecimento.", 
          author: "Albert Einstein" 
        },
        { 
          quote: "O único modo de fazer um ótimo trabalho é amar o que você faz.", 
          author: "Steve Jobs" 
        },
        { 
          quote: "O único que pode definir nosso limite é nós mesmos.", 
          author: "Goku de Dragon Ball" 
        }
      ],
      currentQuote: null,
      currentAuthor: null
    }
  },
  methods: {
    generateQuote() {
      const randomIndex = Math.floor(Math.random() * this.quotes.length);
      const { quote, author } = this.quotes[randomIndex];
      this.currentQuote = quote;
      this.currentAuthor = author;
    }
  },
  mounted() {
    this.generateQuote();
  }
}
</script>

<style scoped>
.quote-wrapper {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;

}

.quote-content {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 8px;
  text-align: center;
}

blockquote {
  margin: 0 0 1.5rem 0;
  padding: 0;
}

.quote-text {
  font-size: 1.25rem;
  font-style: italic;
  color: #2c3e50;
  line-height: 1.6;
}

.quote-author {
  display: block;
  margin-top: 0.5rem;
  font-size: 1rem;
  font-weight: 600;
  color: #42b983;
}

.quote-button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.quote-button:hover {
  background-color: #369f6b;
}
</style>