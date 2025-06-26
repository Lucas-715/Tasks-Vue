<template>
  <div id="container-tarefas">
    <div id="titulo">
      <h1>Minha Lista de Tarefas!</h1>
    </div>

    <div id="adicionar-tarefa">
      <input
        type="text"
        v-model="newTaskText"
        @keyup.enter="addTask"
        placeholder="Adicionar nova tarefa..."
      />
      <button @click="addTask">Adicionar</button>
    </div>

    <div id="lista-tarefas">
      <p v-if="tasks.length === 0" class="mensagem-vazia">
        Parece que você não tem tarefas ainda. Que tal adicionar uma?
      </p>
      <ul>
        <li
          v-for="task in tasks"
          :key="task.id"
          :class="{ completed: task.completed }"
          @click="toggleTaskCompletion(task.id)"
        >
          {{ task.text }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TarefasMelhoradas',
  data() {
    return {
      newTaskText: '', 
      tasks: [
        
        { id: 1, text: 'Estudar POO (Programação Orientada a Objetos)', completed: false },
        { id: 2, text: 'Revisar conceitos de Java', completed: true },
        { id: 3, text: 'Preparar o café!', completed: false }
      ],
      nextTaskId: 4 
    };
  },
  methods: {
    addTask() {
      
      if (this.newTaskText.trim() !== '') {
        this.tasks.push({
          id: this.nextTaskId++, 
          text: this.newTaskText.trim(),
          completed: false 
        });
        this.newTaskText = ''; 
      } else {
        alert('Por favor, digite o texto da tarefa!'); 
      }
    },
    toggleTaskCompletion(taskId) {
      
      const task = this.tasks.find(t => t.id === taskId);
      if (task) {
        task.completed = !task.completed; 
        console.log(`Tarefa '${task.text}' agora está ${task.completed ? 'concluída' : 'pendente'}.`);
      }
    }
  }
};
</script>

<style>

#container-tarefas {
  font-family: 'Arial', sans-serif;
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(255, 255, 255, 0.1);
  background-color: #f9f9f9;
}

#titulo h1 {
  text-align: center;
  color: #000000;
  margin-bottom: 30px;
}

#adicionar-tarefa {
  display: flex;
  gap: 10px;
  margin-bottom: 25px;
}

#adicionar-tarefa input[type="text"] {
  flex-grow: 1;
  padding: 12px 15px;
  border: 1px solid #000000;
  border-radius: 5px;
  font-size: 1rem;
}

#adicionar-tarefa button {
  padding: 12px 20px;
  background-color: #4CAF50; 
  color: rgb(255, 255, 255);
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

#adicionar-tarefa button:hover {
  background-color: #45a049; 
  color: black;
}

#lista-tarefas ul {
  list-style: none;
  padding: 0;
}

#lista-tarefas li {
  background-color: #ffffff;
  color: black;
  padding: 15px;
  margin-bottom: 10px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  display: flex;
  align-items: center;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

#lista-tarefas li:hover {
  background-color: #1c9800;
  color: rgb(255, 255, 255);
}

.completed {
  text-decoration: line-through;
  color: #008b02;
  background-color: #e0e0e0;
}

.mensagem-vazia {
  text-align: center;
  color: #666;
  font-style: italic;
  margin-top: 30px;
}
</style>