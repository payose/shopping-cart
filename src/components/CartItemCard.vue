<template>
  <div class="flex bg-gray-100 border-solid border-4 border-gray-100 my-5">
    <img :src="require(`../assets/images/${product.image}`)" class="max-h-16 md:max-h-28" alt="">
    <div class="text-gray-500 ml-2 md:ml-10 flex flex-col md:flex-row flex-3 justify-between content-center w-4/5">
      <div class="flex flex-wrap content-center">
        <p class=" md:text-xl inline">{{ product.name}}</p>
      </div>
        <div class="flex justify-between items-center"> 
          <button class="p-0 md:py-3 md:px-5 border-solid border-2 border-gray-200" @click="addToCart()">+</button>
          <button class="md:py-3 md:px-5 border-solid border-2 border-gray-200">{{product.quantity }}</button>
          <button class="md:py-3 md:px-5 border-solid border-2 border-gray-200" @click="removeFromCart()">-</button>
        </div>
        <div class="flex flex-wrap content-center mr-3">
        <p class="text-green-500"> Total Cost: <span>&#8358;</span> {{ itemCost.toFixed() }}</p>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  props: [
    'product'
  ],

  computed: {
    itemCost(){
      return this.product.price * this.product.quantity
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
}
</script>