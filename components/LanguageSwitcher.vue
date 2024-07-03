<template>
  <div>
    <button @click="changeLanguage('en')">English</button>
    <button @click="changeLanguage('es')">Español</button>
    <button @click="changeLanguage('fr')">Français</button>
  </div>
</template>

<script setup lang="ts">
import { useStore } from "~/composables/useStore";
import type { Language } from "~/types";

const { setLanguage } = useStore();

function changeLanguage(locale: Language): void {
  setLanguage(locale);
}
</script>
