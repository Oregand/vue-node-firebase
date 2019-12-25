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
                  <nuxt-link :to="userLink(user.id)">Edit</nuxt-link>
                  <nuxt-link to="/">Delete</nuxt-link>
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
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  methods: {
    userLink: (userId) => {
      return `/users/${userId}`
    }
  },
  async asyncData({ $axios }) {
    const users = await $axios.$get(
      'https://5e01296a685ac80014515256.mockapi.io/api/users'
    )
    return { users }
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
