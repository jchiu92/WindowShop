<template>
  <div class="flex w-full">
    <div v-if="businessList" class="flex-grow">
      <div class="mx-auto container pt-10 sm:px-6 xs:px-24 ">
        <div class="flex justify-between w-5xl lg:max-w-6xl py-4 px-6 bg-gray-100 shadow-xs my-5">
          <div class="inline-block relative w-auto">
            <select class="block appearance-none w-full bg-white border border-gray-400 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline">
              <option>Sort By</option>
              <option>Option 2</option>
              <option>Option 3</option>
            </select>
            <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700 text-2xl">
              <span class="mdi mdi-sort" />
            </div>
          </div>
          <div class="inline-block relative w-auto">
            <select class="block appearance-none w-full bg-white border border-gray-400 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline">
              <option>Category</option>
              <option>Option 2</option>
              <option>Option 3</option>
            </select>
            <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700 text-2xl">
              <span class="mdi mdi-menu-down" />
            </div>
          </div>
          <div class="inline-block relative w-auto">
            <select class="block appearance-none w-full bg-white border border-gray-400 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline">
              <option>Shop Type</option>
              <option>Option 2</option>
              <option>Option 3</option>
            </select>
            <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700 text-2xl">
              <span class="mdi mdi-menu-down" />
            </div>
          </div>
          <div class="inline-block relative w-auto">
            <select class="block appearance-none w-full bg-white border border-gray-400 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline">
              <option>Location</option>
              <option>Option 2</option>
              <option>Option 3</option>
            </select>
            <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700 text-2xl">
              <span class="mdi mdi-menu-down" />
            </div>
          </div>
        </div>
        <span class="text-2xl text-black font-bold">
          <span class="underline text-red">1,000</span>
          businesses found
        </span>
        <ListingCard
          v-for="(business, i) in businessList"
          :key="i"
          :business-data="business"
        />
      </div>
    </div>
    <div v-else class="flex-grow">
      <div class="mx-auto container my-4 px-6 xs:px-24 text-center">
        <h1
          v-if="categoryDetails && categoryDetails.label"
          class="m-4 text-4xl font-display"
        >
          There are no businesses listed under {{ categoryDetails.label }} in
          your region. Try changing category or region.
        </h1>
        <h1 v-else>
          There are no businesses listed for this category in your region. Try
          changing category or region.
        </h1>
      </div>
    </div>
  </div>
</template>

<script>
import ListingCard from '~/components/ListingCard'

export default {
  components: {
    ListingCard
  },

  async asyncData ({ $axios }) {
    const businessList = await $axios.$get('https://cms.windowshop.co.nz/_/items/test_business')
    return { businessList: businessList.data }
  },

  data () {
    return {
      categoryDetails: {
        id: '7fb829d8-5ad9-49d3-9af5-a925b782f591',
        label: 'Supermarkets'
      },
      regionId: 'Auckland'
    }
  }
}
</script>

<style></style>
