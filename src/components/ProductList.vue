<template>
  <div>
    <ul>
      <li v-for="product in products" :key="product.id">
        <span v-if="!product.isEditing"
          >{{ product.name }} - ${{ product.price }} -
          {{ product.description }}</span
        >
        <div v-else>
          <input v-model="product.name" />
          <input v-model="product.price" type="number" />
          <textarea v-model="product.description"></textarea>
          <button @click="updateProduct(product)">Update</button>
        </div>
        <button @click="editProduct(product)" class="edit">Edit</button>
        <button @click="deleteProduct(product.id)" class="delete">
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
ul {
  list-style-type: none;
}

button {
  margin: 5px;
}
.edit button {
  ba: orange;
}
.delete button {
  color: red;
}
</style>
