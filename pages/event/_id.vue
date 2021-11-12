<template>
    <div>
        <!-- {{ this.$route.params.id }} -->
        {{ character}}
         {{ character[0].name }}
    </div>
</template>


<script>

export default ({
      async asyncData({ $axios, error, params }) {
    try {
      const response = await $axios.get('https://breakingbadapi.com/api/characters/' + params.id)
      return {
      character: response.data
      }
    } catch (error) {
      error({
      statusCode: 503,
      message: "unable to fetch events at this time. Please try later."
      })
    }
    },
    head() {
      return {
        titleTemplate: 'Event ' + this.id,
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'What you need to know about event #' + this.id
          }
        ]
      }
    },
    computed: {
        id() {
           return this.$route.params.id 
        }
    },
})
</script>
