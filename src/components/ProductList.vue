<template>
  <div class="product-list">
    <ul>
      <li v-for="product in products" :key="product.id" class="product-item">
        <span v-if="!product.isEditing" class="product-info">
          {{ product.name }} - ${{ product.price }} - {{ product.description }}
        </span>
        <div v-else class="edit-form">
          <input v-model="product.name" class="input" />
          <input v-model="product.price" type="number" class="input" />
          <textarea v-model="product.description" class="textarea"></textarea>
          <button @click="updateProduct(product)" class="submit-button">
            Update
          </button>
        </div>
        <button @click="editProduct(product)" class="edit-button">Edit</button>
        <button @click="deleteProduct(product.id)" class="delete-button">
          Delete
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ProductList',
  props: ['products'],
  methods: {
    editProduct(product) {
      product.isEditing = true
    },
    updateProduct(product) {
      product.isEditing = false
      this.$emit('update-product', product)
    },
    deleteProduct(id) {
      this.$emit('delete-product', id)
    },
  },
}
</script>

<style scoped>
.product-list {
  background: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
}

.product-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 15px;
  color: #ffffff;
}

.product-info {
  flex: 1;
}

.edit-form {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.edit-button,
.delete-button {
  margin-left: 10px;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.edit-button {
  background: #4db8ff;
  color: #ffffff;
  transition: background 0.3s;
}

.edit-button:hover {
  background: #80c8ff;
}

.delete-button {
  background: #ff4d4d;
  color: #ffffff;
  transition: background 0.3s;
}

.delete-button:hover {
  background: #ff8080;
}
</style>
