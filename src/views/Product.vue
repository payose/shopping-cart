<template>
  <div>
    <img :src="require(`../assets/images/${product.image}`)" alt="">
    <h3 class="text-center">{{ product.name }}</h3>
      <p class="description">{{product.description }}</p>
      <h3 class="text-center"> ${{ product.price.toFixed(2) }}</h3>
     
     <!-- <div class="cart-total" v-if="productTotal">
        <h3>In Cart</h3>
        <h4> {{ productTotal }}</h4>
      </div> -->

      <div class="button-container"> 
        <button class="remove" @click="removeFromCart()">Remove</button>
        <button class="add" @click="addToCart()">Add</button>
      </div>
  </div>
</template>

<script> 
import { mapState } from 'vuex'

export default {
  computed: {
    ...mapState([
      'product'
    ]),
    productTotal() {
      return this.$store.getters.productQuantity(this.product)
    }
  },

  methods: {
    addToCart() {
      this.$store.commit('addToCart', this.product)
    },

    removeFromCart() {
      this.$store.commit('removeFromCart', this.product)
    }
  }
  // methods: {
    /* back () {
      this.$router.push('/')
    } */

  // }

}
</script>