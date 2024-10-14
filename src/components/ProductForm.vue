<template>
  <form @submit.prevent="addProduct">
    <div>
      <label for="name">Product Name:</label>
      <input v-model="productName" id="name" required />
    </div>
    <div>
      <label for="price">Price:</label>
      <input type="number" v-model="productPrice" id="price" required />
    </div>
    <div>
      <label for="description">Description:</label>
      <textarea v-model="productDescription" id="description" required></textarea>
    </div>
    <button type="submit">Add Product</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      productName: '',
      productPrice: '',
      productDescription: ''
    };
  },
  methods: {
    addProduct() {
      const newProduct = {
        name: this.productName,
        price: this.productPrice,
        description: this.productDescription
      };
      this.$emit('add-product', newProduct);
      this.resetForm();
    },
    resetForm() {
      this.productName = '';
      this.productPrice = '';
      this.productDescription = '';
    }
  }
};
</script>
