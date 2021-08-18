<template>
  <section
    class="text-gray-600 border-b dark:border-gray-700 pb-16 bg-white dark:text-gray-300 dark:bg-dark"
  >
    <div
      class="container max-w-screen-lg mx-auto md:items-start md:text-left items-center py-32 pb-12 flex flex-col px-5"
    >
     

      <div class="font-body">
        <Oss :projects="projects" />
        <!-- <Testimonials /> -->
      </div>

    </div>
  </section>
</template>

<script>
import axios from 'axios'
// import Testimonials from '@/components/home/Testimonials.vue'
import Oss from '@/components/home/Projects.vue'

export default {
  layout: 'default',
  components: {
    // Testimonials,
    Oss,
  },
  asyncData({ params, error }) {
    return axios
      .get(
        'https://api.github.com/search/repositories?q=user:mouadziani%20feautred%20repository%20in:readme&sort=stars&order=desc&per_page=5'
      )
      .then((response) => {
        return {
          projects: response.data.items,
        }
      })
      .catch((errors) => {
        console.log(errors)
      })
  },
}
</script>
