<template>
  <div>
    <div>
      <a href="createTask" class="absolute right-0 top-0 m-4 sm:text-5xl text-4xl">
        <Icon name="ph:plus-circle-light" />
      </a>
    </div>
    <div 
      class="sm:w-1/2 relative overflow-x-auto shadow-md sm:rounded-lg sm:mt-20 mt-10 sm:ml-auto sm:mr-16 lg:mr-64 md:ml-auto">
      <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-purple-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
          <tr>
            <th scope="col" class="px-6 py-3">
              Tarefa
            </th>
            <th scope="col" class="px-6 py-3">
              Prioridade
            </th>
            <th scope="col" class="px-6 py-3">
              Ações
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="task in tasks" :key="task._id"
            class="odd:bg-white odd:dark:bg-gray-900 even:bg-gray-50 even:dark:bg-gray-800 border-b dark:border-gray-700">
            <td scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
              {{ task.task }}
            </td>
            <td v-if="task.priority == 'Baixa'" class="px-6 py-4 text-green-500">
              {{ task.priority }}
            </td>
            <td v-if="task.priority == 'Média'" class="px-6 py-4 text-yellow-500">
              {{ task.priority }}
            </td>
            <td v-if="task.priority == 'Alta'" class="px-6 py-4 text-red-500">
              {{ task.priority }}
            </td>
            <td class="px-6 py-4">
              <button class="font-medium hover:underline mr-3">
                <NuxtLink :to="{ name: 'task-id', params: { id: task._id.toString() } }">
                  <Icon name="ic:outline-mode-edit-outline" class="text-2xl" />
                </NuxtLink>
              </button>
              <button @click="finishTask(task._id.toString())" class="font-medium hover:underline mr-3">
                <Icon name="material-symbols:check-small" class="text-3xl" />
              </button>
              <button @click="deleteTask(task._id.toString())"
              class="font-medium hover:underline">
                <Icon name="material-symbols:delete" class="text-2xl" />
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import apiService from '~/services/apiService.js';
import { ref, onMounted } from 'vue';
const tasks = ref([])

const listTask = async () => {
  try {
    const response = await apiService.incompleteTasks();
    tasks.value = response.data.data.incompleteTasks
  } catch (error) {
    console.error(error)
  }
}
onMounted(listTask)

const finishTask = async (id) => {  
  try {
    const response = await apiService.completedTask({
        id: id,
        status: true
      });
      if (response) {
        alert('Tarefa concluída!')
        listTask()
      }
  } catch (error) {
    console.error(error)
  }
}

const deleteTask = async (id) => {
  try {
    console.log(typeof(id))
    const response = await apiService.deleteTask(id);
      if (response) {
        alert('Tarefa excluída!')
        listTask()
      }
  } catch (error) {
    console.error(error)
  }
}


</script>