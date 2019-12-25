<template>
  <div class="w-full max-w-xs">
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="mb-4">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="username"
        >
          Name
        </label>
        <input
          id="Name"
          v-model="user.user.name"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          type="text"
          placeholder="Name"
        />
      </div>
      <div class="mb-6">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="Email">
          Email
        </label>
        <input
          id="Email"
          v-model="user.user.email"
          class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
          type="email"
          placeholder="Email"
        />
      </div>
      <div class="flex items-center justify-between">
        <p v-if="response" class="text-red-500 text-xs italic">
          {{ response }}
        </p>
      </div>
      <div class="flex items-center justify-between">
        <button
          v-if="user.user.name && user.user.email"
          @click="editUser()"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
        >
          Edit User
        </button>
        <nuxt-link
          class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800"
          to="/"
        >
          Cancel Edit
        </nuxt-link>
      </div>
    </form>
  </div>
</template>
<script>
import VueTypes from 'vue-types'

export default {
  props: {
    user: {
      type: Object,
      default: Function
    }
  },
  data: () => {
    return {
      response: VueTypes.object
    }
  },
  methods: {
    async editUser() {
      const response = await this.$axios.$put(
        `https://5e01296a685ac80014515256.mockapi.io/api/users/${this.user.user.id}`,
        this.user.user
      )

      this.response = response
    }
  }
}
</script>
<style>
.w-full {
  font-size: 1rem;
}
</style>
