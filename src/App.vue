<template>
  <header class="d-flex justify-content-center align-items-center mt-5 mb-5">
    <div class=""><img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /></div>
    <div class="wrapper">
      <h1>Set Up</h1>
    </div>
  </header>

  <main class="row">
    <CreateTask/>
    <ListsTask/>
  </main>
</template>

<script setup>
  import CreateTask from './components/CreateTask.vue';
  import ListsTask from './components/ListsTask.vue';
</script>
