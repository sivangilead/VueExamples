<template>
  <div id="app">
    <example msg="Welcome to Your Vue.js App"/>
    <button>test</button>
  </div>
</template>

<script>
import Example from './components/example.vue'

export default {
  name: 'app',
  components: {
    Example
  }
}
</script>
