<template>
  <div class="w-6xl lg:max-w-6xl py-4 px-6 bg-gray-100 shadow-xs my-5">
    <div class="flex items-center">
      <img
        v-if="businessData && businessLogoUrl"
        class="w-24 h-24 object-contain rounded-sm shadow bg-white"
        :src="businessLogoUrl"
      />
      <img
        v-else
        class="w-24 h-24 object-cover rounded-sm border-2 border-white shadow bg-covid"
        alt="Business Loading"
        src="images/shop.png"
      >
      <div class="flex-col px-2 -my-2">
        <h2 class="text-gray-800 text-3xl font-semibold">
          {{ businessData.business_name }}
        </h2>
        <a
          v-if="businessData.access_physical && businessData.formatted_address"
          :href="'https://www.google.co.nz/maps/search/' +
            businessData.formatted_address"
          class="mt-2 text-sm font-bold text-gray-600 hover:underline"
          target="_blank"
        >
          <span class="mdi mdi-google-maps pr-1" />
          {{ businessData.formatted_address }}
        </a>
        <div class="flex flex-row">
          <a
            v-if="businessData.contact_email"
            :href="'mailto:' +
              businessData.contact_email"
            class="mt-2 w-1/2 text-sm font-bold text-gray-600 hover:underline"
            target="_blank"
          >
            <span class="mdi mdi-at pr-1" />
            {{ businessData.contact_email }}
          </a>

          <a
            v-if="businessData.contact_number"
            :href="'tel:' +
              businessData.contact_number"
            class="mt-2 w-1/2 text-sm font-bold text-gray-600 hover:underline"
            target="_blank"
          >
            <span class="mdi mdi-phone pr-1" />
            {{ businessData.contact_number }}
          </a>
        </div>
      </div>
    </div>
    <p v-if="businessData.description" class="mt-2 text-gray-700 text-justify w-max-130">
      {{ businessData.description }}
    </p>
    <div class="flex flex-wrap -mx-1">
      <div v-if="businessImageUrl[0]" class="my-1 px-1 bg-white">
        <img class="object-cover h-48 w-48" :src="businessImageUrl[0]" />
      </div>
      <div v-if="businessData.image2" class="my-1 px-1 bg-white">
        <img class="object-cover h-48 w-48" :src="businessData.image2" />
      </div>
      <div v-if="businessData.image3" class="my-1 px-1 bg-white">
        <img class="object-cover h-48 w-48" :src="businessData.image3" />
      </div>
      <div v-if="businessData.image4" class="my-1 px-1 bg-white">
        <img class="object-cover h-48 w-48" :src="businessData.image4" />
      </div>
      <div v-if="businessData.image5" class="my-1 px-1 bg-white">
        <img class="object-cover h-48 w-48" :src="businessData.image5" />
      </div>
    </div>

    <div class="flex flex-wrap justify-end mt-6">
      <div>
        <a
          v-if="businessData.facebook"
          :href="businessData.facebook"
          class="text-md font-medium text-gray-900 ml-4 hover:underline"
          target="_blank"
        >
          <span class="mdi mdi-facebook-box pr-1" />Facebook
        </a>
        <a
          v-if="businessData.instagram"
          :href="businessData.instagram"
          class="text-md font-medium text-gray-900 ml-4 hover:underline"
          target="_blank"
        >
          <span class="mdi mdi-instagram pr-1" />Instagram
        </a>
      </div>
      <div>
        <a
          v-if="businessData.access_online"
          :href="businessData.shopping_url"
          class="text-md font-medium text-gray-900 ml-4 hover:underline"
          target="_blank"
        >
          <span class="mdi mdi-shopping pr-1" />Shop Online
        </a>

        <a
          v-if="businessData.url"
          :href="businessData.url"
          class="text-md font-medium text-gray-900 ml-4 hover:underline"
          target="_blank"
        >
          <span class="mdi mdi-web pr-1" />Visit Website
        </a>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      businessLogoUrl: false,
      businessImageUrl: []
    //   businessImage2Url: false,
    //   businessImage3Url: false,
    //   businessImage4Url: false,
    //   businessImage5Url: false
    }
  },
  async mounted () {
    let result = await this.$axios.$get('https://cms.windowshop.co.nz/_/files/' + this.businessData.business_logo)
    this.businessLogoUrl = result.data.data.full_url
    result = await this.$axios.$get('https://cms.windowshop.co.nz/_/items/test_business_directus_files?filter[test_business_id]=' + this.businessData.id)

    // for ( image in result) {
    //   console.log('Iterate', image)
    //   // result = await this.$axios.$get('https://cms.windowshop.co.nz/_/files/' + result.data[i].directus_files_id)
    //   // this.businessImageUrl[i] = result.data.data.full_url
    // }

    result = await this.$axios.$get('https://cms.windowshop.co.nz/_/files/' + result.data[0].directus_files_id)
    this.businessImageUrl[0] = result.data.data.full_url
    console.log('Business image ID', this.businessImageUrl)
  },

  props: {
    businessData: {
      type: Object,
      required: true
    }
  }
}
</script>

<style></style>
