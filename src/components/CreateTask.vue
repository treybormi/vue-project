<template>
  <aside class="col-6 border-end border-success border-2">
      <p class="input-group"><span class="input-group-text">Give link:</span><input v-model="url" type="text" class="form-control" placeholder="https://www.facebook.com"/></p>
      <p>Choose the time:</p>
      <div class="d-flex flex-wrap">
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="0" />
          <span class="form-check-label">Every Minute</span>
        </p>
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="1" />
          <span class="form-check-label">Every Hour</span>
        </p>
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="2" />
          <span class="form-check-label">Every Day</span>
        </p>
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="3" />
          <span class="form-check-label">Every Week</span>
        </p>
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="4" />
          <span class="form-check-label">Every Month</span>
        </p>
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="5" />
          <span class="form-check-label">Every Quarterly</span>
        </p>
        <p class="form-check me-4">
          <input class="form-check-input" type="radio" v-model="pick" value="6" />
          <span class="form-check-label">Every Year</span>
        </p>
      </div>
      <button class="btn btn-success mt-3" type="submit" @click="createTasks">Create</button>
    </aside>
</template>

<script setup>
  import axios from 'axios'
  import { ref } from 'vue'

  const url = ref('')
  const pick = ref()

  const createTasks = () => {
    console.log(url.value, pick.value)
    axios.post("http://127.0.0.1:8000/api/schedule",{url:url.value, expression:pick.value})
    .then(response => alert(response))
    .catch(error => console.log(error))
  }
</script>