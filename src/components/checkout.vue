<template>
    <div>
    <h2>Checkout</h2>
    <h3>Added products</h3>
    <div v-for='product in cart' :key="product.id">
        {{product.title}} 
        <button @click='removeProduct(product)'>remove</button>
    </div>
    <p>
      <strong> Name </strong> <input v-model="name" />
      <strong> Address </strong> <input v-model="address" />
      <button> Submit </button>
</p> </div>  
</template>

<script>
export default {
name: "myCheckout",
props: ["cart"], 
data(){
    return {
        s_p : !(this.show_products),
        name: "",
        address: "",
          order:
            {
                first_name:'',
                last_name: '',
                phone_number: '',
                postcode: '',
                address: '',
                items: []
            },
    }
},
methods: {
removeProduct(product) {
    this.$emit('removeProduct',product )
}
}
};
</script>
