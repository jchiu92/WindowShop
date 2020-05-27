<template>
  <div class="flex flex-col min-h-screen min-w-full items-stretch">
    <!--Nav-->
    <div>
      <NavBar />
    </div>

    <!--Container-->
    <div class="pt-10 bg-mainbg">
      <nuxt />
    </div>

    <!-- Footer -->
    <footer class="w-full bottom-0 bg-gray-900 p-2">
      <div class="container mx-auto">
        <div
          class="flex flex-wrap-reverse md:flex-wrap items-center md:justify-between justify-center items-start"
        >
          <div
            id="nav-content"
            class="bg-white lg:bg-transparent text-black p-4 lg:p-0 z-20"
          >
            <a
              class="mx-auto lg:mx-0 hover:underline text-black rounded-full mt-4 lg:mt-0 py-1 px-4 lg:px-6 bg-white"
              href="https://centricmedia.typeform.com/to/RIYYpD"
              target="_blank"
            >
              List Your Business
              <span class="mdi mdi-open-in-new" />
            </a>
          </div>
          <div class="w-full sm:w-6/12 px-4">
            <ul class="flex flex-wrap list-none md:justify-end justify-center">
              <li>
                <nuxt-link
                  to="/"
                  class="text-white hover:text-gray-400 text-sm font-semibold block py-2 px-3"
                >
                  Home
                </nuxt-link>
              </li>
              <li>
                <nuxt-link
                  to="/about"
                  class="text-white hover:text-gray-400 text-sm font-semibold block py-2 px-3 hidden"
                >
                  About
                </nuxt-link>
              </li>
              <li>
                <nuxt-link
                  to="/fag"
                  class="text-white hover:text-gray-400 text-sm font-semibold block py-2 px-3"
                >
                  FAQ
                </nuxt-link>
              </li>
              <li>
                <nuxt-link
                  to="/legal/privacy"
                  class="text-white hover:text-gray-400 text-sm font-semibold block py-2 px-3"
                >
                  Privacy Policy
                </nuxt-link>
              </li>
              <li>
                <nuxt-link
                  to="/legal/terms-and-conditions"
                  class="text-white hover:text-gray-400 text-sm font-semibold block py-2 px-3"
                >
                  T&Cs
                </nuxt-link>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import NavBar from '~/components/NavBar'

export default {
  components: {
    NavBar
  }
}
</script>

<style></style>
