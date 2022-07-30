<template>
  <div id="app">
    <Form mail="Email" passwor="Password" />
  </div>
</template>

<script>
import Form from './components/Form.vue';
export default {
  name: 'App',
  components: {
    Form,
  },
};
</script>
