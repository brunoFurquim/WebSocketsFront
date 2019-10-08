<template>
  <div id="app">
    <Form></Form>
  </div>
</template>

<script>
import Form from "./Form";

export default {
  name: "app",
  components: {
    Form
  }
};
</script>

<style>
#app {
  min-height: 100vh !important;
  min-width: 100vh !important;
  position: fixed;
  
}
</style>
