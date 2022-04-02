<template>
  <div id="app">
    <header>
      <h1>{{sitename}}</h1>
      <button @click="showCheckout">{{this.cart.leangth}} Checkout</button>
    </header>
    <product-list :products='products' @addProduct="addToCart" v-show= show_products></product-list>
    <checkout :cart='cart' @removeProduct='removeFromCart' ></checkout>
  </div>
</template>

<script>
import productList from './components/productlist.vue'
import checkout from './components/checkout.vue'

export default {
  name: 'app',
  components: {productList, checkout},
  data(){
    return{
      sitename: 'Lesson store',
      cart:[],
      products: [],
      show_products:true,
     // lessons: [], https://cw3-main.herokuapp.com/collection/products

    }
  },
  //GET request mangodb
  created: function () {
  fetch('https://cw3-main.herokuapp.com/collection/products')
    .then(response => response.json())
    .then(data => this.products = data)
    .catch(err=> console.log(err.message))
  },

  methods: {
    showCheckout() {}, // add same code like cw1 
    addToCart(product){
      this.cart.push(product);
      product.availableInventory --
    },
    removeFromCart(product){
      this.cart.forEach(product2 => {
        if (product2.id === product.id) {
          product.availableInventory++
          this.cart.splice(this.cart.indexOf(product),1)
        }
      })
    }
  }
}
</script>
<style>

#app{
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
margin-top:60px;
}
</style>

