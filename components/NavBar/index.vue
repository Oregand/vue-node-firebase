<template>
  <header class="bg-gray-900">
    <div class="flex items-center justify-between px-4 py-3">
      <div>
        <img class="h-8" src="/img/logo-inverted.svg" alt="Workcation" />
      </div>
      <div>
        <button
          @click="isOpen = !isOpen"
          type="button"
          class="block text-gray-500 hover:text-white focus:text-white focus:outline-none"
        >
          <svg class="h-6 w-6 fill-current" viewBox="0 0 24 24">
            <path
              v-if="isOpen"
              fill-rule="evenodd"
              d="M18.278 16.864a1 1 0 0 1-1.414 1.414l-4.829-4.828-4.828 4.828a1 1 0 0 1-1.414-1.414l4.828-4.829-4.828-4.828a1 1 0 0 1 1.414-1.414l4.829 4.828 4.828-4.828a1 1 0 1 1 1.414 1.414l-4.828 4.829 4.828 4.828z"
            />
            <path
              v-if="!isOpen"
              fill-rule="evenodd"
              d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
            />
          </svg>
        </button>
      </div>
    </div>
    <div :class="isOpen ? 'block' : 'hidden'" class="px-2 pt-2 pb-4">
      <nuxt-link
        class="block px-2 py-1 text-white font-semibold rounded hover:bg-gray-800"
        to="/"
        >Home page</nuxt-link
      >
      <nuxt-link
        class="block px-2 py-1 text-white font-semibold rounded hover:bg-gray-800"
        to="/users"
        >User List</nuxt-link
      >
      <nuxt-link
        class="block px-2 py-1 text-white font-semibold rounded hover:bg-gray-800"
        to="/users/new"
        >Create New user</nuxt-link
      >
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false
    }
  }
}
</script>
