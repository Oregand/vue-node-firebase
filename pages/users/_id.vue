<template>
  <div class="container">
    <div>
      <div class="flex flex-wrap">
        <div class="w-full">
          <button
            @click="flags.isEdit = !flags.isEdit"
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
          >
            Edit User
          </button>
        </div>
        <div class="w-full">
          <div
            v-if="flags.isEdit"
            class="max-w-sm w-full lg:max-w-full lg:flex"
          >
            <div
              class="h-48 lg:h-auto lg:w-48 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden"
              style="background-image: url('/img/card-left.jpg')"
              title="Woman holding a mug"
            />
            <div
              class="border-r border-b border-l border-gray-400 lg:border-l-0 lg:border-t lg:border-gray-400 bg-white rounded-b lg:rounded-b-none lg:rounded-r p-4 flex flex-col justify-between leading-normal"
            >
              <div class="mb-8">
                <p class="text-sm text-gray-600 flex items-center">
                  <svg
                    class="fill-current text-gray-500 w-3 h-3 mr-2"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 20 20"
                  >
                    <path
                      d="M4 8V6a6 6 0 1 1 12 0v2h1a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2v-8c0-1.1.9-2 2-2h1zm5 6.73V17h2v-2.27a2 2 0 1 0-2 0zM7 6v2h6V6a3 3 0 0 0-6 0z"
                    />
                  </svg>
                </p>
                <div class="text-gray-900 font-bold text-xl mb-2">
                  {{ user.ID }}
                </div>
                <p class="text-gray-700 text-base">
                  {{ user.email }}
                </p>
              </div>
              <div class="flex items-center">
                <img
                  :src="user.avatar"
                  class="w-10 h-10 rounded-full mr-4"
                  alt="Avatar of Jonathan Reinink"
                />
                <div class="text-sm">
                  <p class="text-gray-900 leading-none">{{ user.name }}</p>
                  <p class="text-gray-600">{{ user.createdAt }}</p>
                </div>
              </div>
            </div>
          </div>
          <EditUserForm v-if="!flags.isEdit" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueTypes from 'vue-types'

import EditUserForm from '~/components/EditUserForm/index.vue'

export default {
  components: {
    EditUserForm
  },
  data: () => {
    return {
      flags: {
        isEdit: VueTypes.bool.def(false)
      }
    }
  },
  async asyncData({ $axios, params }) {
    const user = await $axios.$get(
      `https://5e01296a685ac80014515256.mockapi.io/api/users/${params.id}`
    )
    return { user }
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
