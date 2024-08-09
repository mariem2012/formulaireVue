<template>
  <div id="app">
    <UserForm />
  </div>
</template>

<script>
import UserForm from './components/UserForm.vue';

export default {
  components: {
    UserForm
  }
};
</script>

<style>
    #app {
      display: flex;
      align-items:center;
      justify-content: center;
      background-color: burlywood;
      border-radius: 7px;
      background-color: #0C2C43;
      color: #ffffff;

    }
</style>