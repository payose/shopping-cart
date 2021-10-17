<template>
  <div class="home">
    <div class="container">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
        <Cards
        v-for="product in products" :key="product.id"
        :product="product">
        </Cards>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import Cards from '@/components/Cards.vue'
// import { mapMutations } from 'vuex'
import { mapState } from 'vuex'

export default {
  components: {
    Cards
  },

  methods: {
  },

  computed: {
    ...mapState([
      'products'
    ]),

    // ...mapMutations([
    //   'fetchMoreMovies'
    // ])
  },

  mounted () {
    
  }
}
</script>
