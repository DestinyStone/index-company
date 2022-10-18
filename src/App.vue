<template>
  <div id="app">
    <index/>
  </div>
</template>

<script>
import Index from "./components/home/index";

export default {
  name: 'App',
  components: {
    Index,
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
</style>
