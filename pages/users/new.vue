<template>
  <div class="container">
    <div>
      <logo />
      <CreateUserForm />
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import CreateUserForm from '~/components/CreateUserForm/index.vue'

export default {
  components: {
    Logo,
    CreateUserForm
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
