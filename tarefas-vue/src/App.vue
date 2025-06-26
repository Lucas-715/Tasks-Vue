<template>
  <main class="app-container">
    <header class="app-header">
      <h1 class="app-title">Tarefas com Vue.js</h1>
    </header>

    <section class="components-grid">
      <article class="component-card" id="citacao-container">
        <h2 class="component-title">Citações Inspiradoras</h2>
        <Citacao />
      </article>

      <article class="component-card" id="filtragem-container">
        <h2 class="component-title">Filtro de Conteúdo</h2>
        <Filtragem />
      </article>

      <article class="component-card" id="tarefas-container">
        <h2 class="component-title">Gerenciador de Tarefas</h2>
        <TarefasMelhoradas />
      </article>
    </section>
  </main>
</template>

<script>
import Citacao from './components/Citacao.vue'
import Filtragem from './components/Filtragem.vue'
import TarefasMelhoradas from './components/TarefasMelhoradas.vue'

export default {
  name: 'App',
  components: {
    Citacao,
    Filtragem,
    TarefasMelhoradas
  }
}
</script>

<style scoped>
.app-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.app-header {
  text-align: center;
  margin-bottom: 2rem;
}

.app-title {
  font-size: 2rem;
  color: #2c3e50;
}

.components-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.component-card {
  padding: 1.5rem;
  background: #ffffff;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.component-title {
  margin-bottom: 1rem;
  font-size: 1.25rem;
  color: #42b983;
  border-bottom: 2px solid #f3f3f3;
  padding-bottom: 0.5rem;
}
</style>