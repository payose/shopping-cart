<template>
  <div class="flex items-center mx-5 md:mx-10">
    <img :src="require(`../assets/images/${product.image}`)" alt="" >
    <div class="md:ml-10 ">
      <h3 class="">{{ product.name }}</h3>
      <p class="leading-9">{{product.description }}</p>
      <h3 class=""> <span>&#8358;</span> {{ product.price.toFixed(2) }}</h3>
     
     <!-- <div class="cart-total" v-if="productTotal">
        <h3>In Cart</h3>
        <h4> {{ productTotal }}</h4>
      </div> -->

      <div class="flex justify-between items-center"> 
        <button class="hoverred-700 focus:bg-green-700 focus:outline-none shadow-sm bg-green-500 rounded-sm py-2 px-6" @click="addToCart()">Add</button>
        <button class="hover:bg-red-700 focus:bg-red-700 focus:outline-none shadow-sm bg-red-500 rounded-sm py-2 px-6" @click="removeFromCart()">Remove</button>
      </div>
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