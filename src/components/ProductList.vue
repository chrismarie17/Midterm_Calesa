<template>
  <div>
    <ul>
      <li v-for="(product, index) in products" :key="index">
        <h3>{{ product.name }}</h3>
        <p>Price: {{ product.price }}</p>
        <p>{{ product.description }}</p>
        <button @click="editProduct(index)">Edit</button>
      </li>
    </ul>
    <div v-if="editingIndex !== null">
      <ProductForm
        @add-product="updateProduct"
        :product="products[editingIndex]"
      />
    </div>
  </div>
</template>

<script>
import ProductForm from './ProductForm.vue';

export default {
  components: {
    ProductForm
  },
  props: {
    products: Array
  },
  data() {
    return {
      editingIndex: null
    };
  },
  methods: {
    editProduct(index) {
      this.editingIndex = index;
    },
    updateProduct(updatedProduct) {
      this.$emit('update-product', { index: this.editingIndex, product: updatedProduct });
      this.editingIndex = null;
    }
  }
};
</script>
