<template>
  <div class="container">
    <h1 class="text-center my-4">Gestion des tâches</h1>
    <div class="mb-3">
      <input v-model="newTaskTitle" class="form-control" placeholder="Titre de la tâche" />
      <input v-model="newTaskDescription" class="form-control mt-2" placeholder="Description de la tâche" />
      <button @click="addTask" class="btn btn-primary mt-3">Ajouter Tâche</button>
    </div>
    <ul class="list-group">
      <li v-for="(task, index) in tasks" :key="index" class="list-group-item d-flex justify-content-between align-items-center">
        <span :class="{ completed: task.completed }">{{ task.title }} - {{ task.description }}</span>
        <i @click="toggleTask(index)" class="fas fa-check-circle " role="button"></i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { title: "Tâche 1", description: "Description 1", completed: false },
        { title: "Tâche 2", description: "Description 2", completed: false }
      ],
      newTaskTitle: "",
      newTaskDescription: ""
    };
  },
  methods: {
    addTask() {
      if (this.newTaskTitle && this.newTaskDescription) {
        this.tasks.push({
          title: this.newTaskTitle,
          description: this.newTaskDescription,
          completed: false
        });
        this.newTaskTitle = "";
        this.newTaskDescription = "";
      }
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    }
  }
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
  color: gray;
}
.btn-primary {
  background-color: #017FC0;
  border-color: #017FC0;
}
.btn-primary:hover {
  background-color: #015f8d;
  border-color: #015f8d;
}
</style>
