<template>
    <aside class="col-6 border-start border-success border-2">
        <div v-if="tasksList" class="d-flex justify-content-center">
            <table>
                <thead>
                    <th  class="text-center">Task ID</th>
                    <th class="text-center">Links to Ping</th>
                    <th class="text-center">Scheduled For</th>
                </thead>
                <tr v-for="task in tasksList" :key="task">
                    <td class="text-center">{{ task.id }}</td>
                    <td>{{ task.urls }}</td>
                    <td>{{ task.scheduled }}</td>
                </tr>
            </table>
        </div>
        <div v-else>
            <p>Loading...</p>
        </div>
    </aside>
</template>

<script setup>
    import axios from 'axios'
    import { ref } from 'vue'

    const tasksList = ref(null)

    const getTasks = async () => {
        await axios.get("http://127.0.0.1:8000/api/schedule-lists")
        .then(response => { tasksList.value = response.data })
        .catch(error => console.log(error))}

    getTasks()
</script>
