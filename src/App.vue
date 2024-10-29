<template>
  <div id="app">
    <TaskManager />
  </div>
</template>

<script>
import Vue from 'vue';
import TaskManager from './components/TaskManager.vue';

export default Vue.extend ({
  name: 'App',
  components: {
    TaskManager
  }
},
)
</script>

<style>

</style>
