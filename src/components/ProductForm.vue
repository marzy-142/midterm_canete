<template>
  <form @submit.prevent="submitForm">
    <center>
      <div class="container">
        <label>Product Name:</label>
        <input v-model="productName" required />
      </div>
      <div>
        <label>Price:</label>

        <input v-model="price" type="number" required />
      </div>
      <div>
        <label>Description:</label>
        <textarea v-model="description" required></textarea>
      </div>
    </center>
    <button type="submit">Add Product</button>
  </form>
</template>

<script>
export default {
  name: 'ProductForm',
  data() {
    return {
      productName: '',
      price: '',
      description: '',
    }
  },
  methods: {
    submitForm() {
      const product = {
        id: Date.now(),
        name: this.productName,
        price: this.price,
        description: this.description,
      }
      this.$emit('add-product', product)
      this.productName = ''
      this.price = ''
      this.description = ''
    },
  },
}
</script>

<style scoped>
/* form { */
/* display: flex;
  flex-direction: column;
  justify-content: center; */
/* margin-bottom: 20px;
  padding: 30px;
  text-align: left;
  align-items: center;
  border: 1px solid black;
  width: 30%;
}
/* .container {
  text-align: center;
} */

/* form {
  text-align: left;
  align-items: center;
  border: 1px solid black;
  width: 30%;
} */

div {
  margin-bottom: 20px;
  padding: 30px;
  text-align: left;
  align-items: center;
  border: 1px solid black;
  width: 30%;
}
</style>
