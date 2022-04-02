<template>
  <main>
    <div v-for="product in products" :key="product.id">
      <div id="product_all">
      <h2>{{product.title}}</h2>
      <figure>
        <img v-bind:src="product.image" />
      </figure>
      <p>Subject: {{product.subject}}</p>
      <p>Location: {{product.location}}
      <p>Price: {{ product.price }}</p>
      <p>Available spaces: {{ product.availableInventory }}</p>
      <button @click="addToCart(product)">Add to cart</button>
    </div>
    </div>
  </main>
</template>

<script>
export default {
    name: 'ProductList',
    props: ['products'], 
    data(){
        return {}
    },
    methods: {
        addToCart(product){
            this.$emit('addProduct',product) 
        }
    }
}
</script>
