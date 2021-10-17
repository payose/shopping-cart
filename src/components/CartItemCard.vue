<template>
  <div class="cart-item-card">
    <div class="header">
      <h3>{{ product.name}}</h3>
      <h4> In Cart: {{product.quantity }}</h4>
      <h4> Total Cost: <span>&#8358;</span> {{ itemCost.toFixed() }}</h4>
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
  }
}
</script>