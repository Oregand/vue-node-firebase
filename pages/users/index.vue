<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        User List
      </h1>
      <div class="flex flex-wrap">
        <div class="w-full">
          <table class="table-auto">
            <thead>
              <tr>
                <th class="px-4 py-2">ID</th>
                <th class="px-4 py-2">Name</th>
                <th class="px-4 py-2">Email</th>
                <th class="px-4 py-2">Avatar</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in users">
                <td class="border px-4 py-2">{{ user.id }}</td>
                <td class="border px-4 py-2">{{ user.name }}</td>
                <td class="border px-4 py-2">{{ user.email }}</td>
                <td class="border px-4 py-2">
                  <img :src="user.avatar" alt="avatar" />
                </td>
                <td class="border px-4 py-2">
                  <nuxt-link
                    :to="userLink(user.id)"
                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
                  >
                    Edit
                  </nuxt-link>
                  <button
                    @click="deleteUser(user.id)"
                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
                  >
                    Delete
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueTypes from 'vue-types'

import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data: () => {
    return {
      response: VueTypes.object.def()
    }
  },
  async asyncData({ $axios }) {
    const users = await $axios.$get(
      'https://5e01296a685ac80014515256.mockapi.io/api/users'
    )
    return { users }
  },
  methods: {
    userLink: (userId) => {
      return `/users/${userId}`
    },
    async deleteUser(userId) {
      const response = await this.$axios.$delete(`
        https://5e01296a685ac80014515256.mockapi.io/api/users/${userId}
      `)
      this.response = response
    }
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

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.w-full {
  height: 50vh;
  overflow-y: scroll;
}
</style>
