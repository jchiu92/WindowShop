<template>
  <header class="fixed top-0 w-full bg-gray-900 sm:flex sm:justify-between sm:items-center sm:px-4 sm:py-3">
    <div class="flex items-center justify-between px-4 py-3 sm:p-0">
      <nuxt-link class="flex items-end" to="/">
        <img class="h-8" src="/images/icon.png" />
        <span class="text-white text-2xl font-bold ml-2">windowshop</span>
      </nuxt-link>
      <div class="sm:hidden">
        <button
          type="button"
          class="block text-gray-500 hover:text-white focus:text-white focus:outline-none"
          @click="isOpen = !isOpen"
        >
          <div class="text-2xl">
            <span v-if="!isOpen" class="mdi mdi-menu" />
            <span v-if="isOpen" class="mdi mdi-window-close" />
          </div>
        </button>
      </div>
    </div>
    <nav :class="isOpen ? 'block' : 'hidden'" class="px-2 pt-2 pb-4 sm:flex sm:p-0">
      <nuxt-link
        to="#"
        class="block px-2 py-1 text-white font-semibold rounded hover:bg-gray-800"
      >
        List your business
      </nuxt-link>
      <nuxt-link
        to="/about"
        class="mt-1 block px-2 py-1 text-white font-semibold rounded hover:bg-gray-800 sm:mt-0 sm:ml-2"
      >
        About
      </nuxt-link>
    </nav>
  </header>
</template>

<script>
export default {
  data () {
    return {
      isOpen: false
    }
  }
}
</script>
