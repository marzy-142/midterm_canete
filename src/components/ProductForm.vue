<template>
  <form @submit.prevent="submitForm" class="product-form">
    <div class="form-field">
      <label>Product Name:</label>
      <input v-model="productName" required class="input" />
    </div>
    <div class="form-field">
      <label>Price:</label>
      <input v-model="price" type="number" required class="input" />
    </div>
    <div class="form-field">
      <label>Description:</label>
      <textarea v-model="description" required class="textarea"></textarea>
    </div>
    <button type="submit" class="submit-button">Add Product</button>
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
      this.resetForm()
    },
    resetForm() {
      this.productName = ''
      this.price = ''
      this.description = ''
    },
  },
}
</script>

<style scoped>
.product-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: rgba(255, 255, 255, 0.1);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
}

.form-field {
  margin-bottom: 20px;
  width: 50%;
}

.input,
.textarea {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  border-radius: 5px;
  border: none;
  background: rgba(255, 255, 255, 0.2);
  color: #ffffff;
  font-family: 'Roboto', sans-serif;
}

.input:focus,
.textarea:focus {
  outline: none;
  border: 1px solid #4db8ff;
}

.submit-button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background: #4db8ff;
  color: #ffffff;
  cursor: pointer;
  transition: background 0.3s;
}

.submit-button:hover {
  background: #80c8ff;
}
</style>
