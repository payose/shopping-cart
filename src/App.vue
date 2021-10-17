<template>
  <div class="app w-screen">
    <div id="nav" class="flex justify-between items-center px-10 py-10 w-full h-12 bg-white p-6 mb-12">
      <router-link to="/" class="bg-green-500 rounded-sm py-2 px-6">Home</router-link> 
      <router-link to="/cart" class="bg-green-500 rounded-sm py-2 px-6">Cart</router-link>
      <!-- <router-link to="/product"></router-link> -->
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
   mounted(){
    this.$store.commit('updateCartFromLocalStorage')
  }
}
</script>

<style>

#nav a {
  font-weight: bold;
  color:black
}

#nav a.router-link-exact-active {
  color: #fff;
}
</style>
