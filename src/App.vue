<template>
  <div id="todo-list">
    <div class="container">
      <div class="row bg-white mt-5 p-3 rounded">
        <h3>TODO List do {{name}}</h3>
        <hr>

        <div class="d-flex justify-content-between gap-1 mb-3">
          <input
            v-model="newTask"
            type="text" 
            class="form-control" 
            placeholder="Nova tarefa"
          >

          <button 
            class="btn btn-primary" 
            @click="addTask"
          >
            Adicionar
          </button>
        </div>

        <div class="d-flex flex-column gap-2">
          <div 
            class="card"
            v-for="(task, index) in tasks"
            :key="index"
            @click="task.done = !task.done"
          >
            <div class="card-body d-flex justify-content-between">
              <div class="d-flex gap-2 align-items-center">
                <input type="checkbox" v-model="task.done">
                <h5 class="card-title m-0">{{task.title}}</h5>
              </div>

              <p class="card-text fw-bolder">
                <span v-if="task.done" class="text-success">Concluído</span>
                <span v-else class="text-danger">Pendente</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const name = ref('Matheus');
const tasks = ref([
  { title: 'Estudar VueJS', done: false },
  { title: 'Praticar Vue!', done: false },
]);

const newTask = ref('');
const addTask = () => {
  tasks.value.push({ title: newTask.value, done: false });
  newTask.value = '';
};

</script>

<style>
#todo-list {
  background-color: #f8f8f8;
  width: 100%;
  height: 100vh;
  position: absolute;
}
</style>
