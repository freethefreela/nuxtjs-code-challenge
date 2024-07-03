<script setup lang="ts">
import { reactive } from "vue";
import type { Product } from "~/types";

const emit = defineEmits<{
  (e: "add-product", product: Omit<Product, "id">): void;
}>();

const product = reactive<Omit<Product, "id">>({
  name: "",
  price: 0,
  description: "",
});

function submitForm() {
  emit("add-product", { ...product });
  product.name = "";
  product.price = 0;
  product.description = "";
}
</script>

<template>
  <form @submit.prevent="submitForm">
    <input v-model="product.name" placeholder="Product Name" required />
    <input
      v-model.number="product.price"
      type="number"
      placeholder="Price"
      required
    />
    <textarea
      v-model="product.description"
      placeholder="Description"
      required
    ></textarea>
    <button type="submit">Add Product</button>
  </form>
</template>
