<template>
  <div class="flex bg-gray-100 border-solid border-4 border-gray-100 my-5">
    <img :src="require(`../assets/images/${product.image}`)" class="max-h-8 md:max-h-28" alt="">
    <div class="text-gray-500 ml-10 flex flex-3 justify-between w-4/5">
      <p class=" text-xl align-middle inline">{{ product.name}}</p>
      <div class="flex justify-between items-center"> 
        <button class="py-3 px-5 border-solid border-2 border-gray-200" @click="addToCart()">+</button>
        <button class="py-3 px-5 border-solid border-2 border-gray-200">{{product.quantity }}</button>
        <button class="py-3 px-5 border-solid border-2 border-gray-200" @click="removeFromCart()">-</button>
      </div>
      <p class="text-green-500"> Total Cost: <span>&#8358;</span> {{ itemCost.toFixed() }}</p>
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