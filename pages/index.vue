<template>
  <!-- <Tutorial/> -->
  <div>
    <h1>Events</h1>
    <div class="grid grid-cols-3 gap-10">
      <CharacterCard 
        v-for="(character, index) in characters"
        :key="index"
        :event="character"
        :data-index="index"
      />
    </div>
  </div>
</template>
<script>
import CharacterCard from '@/components/CharacterCard'
export default {
  components:{
    CharacterCard 
  },
  // asyncData({$axios}) {
  //   return $axios.get('https://breakingbadapi.com/api/characters').then(response => {
  //     return {
  //       characters: response.data
  //     }).catch(e => {
  //         error({ statusCode: 503, message: 'Unable to fetch events at this time, please try again' })
  //       })
  //     },
  //   })
  // },
  async asyncData({ $axios, error }) {
    try {
      const response = await $axios.get('https://breakingbadapi.com/api/characters')
      return {
        characters: response.data
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
      title: 'Event Listing',
    }
  },
}
</script>
