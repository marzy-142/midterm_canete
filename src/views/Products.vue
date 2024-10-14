<template>
  <div>
    <h2>Products</h2>
    <nav>
      <router-link to="/home">Home</router-link> |
      <router-link to="/products">Products</router-link>
    </nav>
    <ProductForm @add-product="addProduct" />
    <ProductList
      :products="products"
      @update-product="updateProduct"
      @delete-product="deleteProduct"
    />
  </div>
</template>

<script>
import ProductForm from '../components/ProductForm.vue'
import ProductList from '../components/ProductList.vue'

export default {
  name: 'Products',
  components: {
    ProductForm,
    ProductList,
  },
  data() {
    return {
      products: [],
    }
  },
  methods: {
    addProduct(product) {
      this.products.push(product)
    },
    updateProduct(updatedProduct) {
      const index = this.products.findIndex(
        product => product.id === updatedProduct.id,
      )
      if (index !== -1) {
        this.products.splice(index, 1, updatedProduct)
      }
    },
    deleteProduct(id) {
      this.products = this.products.filter(product => product.id !== id)
    },
  },
}
</script>

<style scoped>
div {
  font-family: 'Courier New', Courier, monospace;
}
h2 {
  margin-bottom: 10px;
}
</style>
