<script setup lang="ts">
import AddProductForm from "~/components/AddProductForm.vue";
import ProductList from "~/components/ProductList.vue";
import LanguageSwitcher from "~/components/LanguageSwitcher.vue";
import type { Product } from "~/types";

const { $client } = useNuxtApp();

const products =
  (await $client.getProducts.useQuery().catch(console.warn)) ?? [];

async function handleAddProduct(product: Omit<Product, "id">) {
  await $client.addProduct.mutate(product);

  products.push(product);
}
</script>

<template>
  <div>
    <h1>Welcome</h1>
    <p>Intro</p>
    <ProductList :products="products" />
    <AddProductForm @add-product="handleAddProduct" />
    <language-switcher />
  </div>
</template>
