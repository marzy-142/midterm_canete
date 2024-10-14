<template>
  <div class="products-container">
    <h2 class="products-title">Products</h2>
    <nav class="nav">
      <router-link to="/home" class="nav-link">Home</router-link>
      <span class="nav-separator">|</span>
      <router-link to="/products" class="nav-link">Products</router-link>
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
  // eslint-disable-next-line vue/multi-word-component-names
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
.products-container {
  background: linear-gradient(135deg, #1e1e2f, #2a2a45);
  color: #ffffff;
  font-family: 'Roboto', sans-serif;
  padding: 40px;
  border-radius: 15px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
}

.products-title {
  text-align: center;
  margin-bottom: 20px;
}

.nav {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.nav-link {
  color: #4db8ff;
  text-decoration: none;
  font-size: 1.2rem;
  margin: 0 10px;
  transition: color 0.3s;
}

.nav-link:hover {
  color: #80c8ff;
}

.nav-separator {
  color: #ffffff;
}
</style>
