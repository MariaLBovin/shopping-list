<script setup lang="ts">
import { ref } from 'vue';
import { IShoppingList } from "../models/IShoppingList";

interface IBasketListProps {
    product: IShoppingList
}

const props = defineProps<IBasketListProps>();


</script>

<template>
<div>
    <ul>
      <li >
        <p>{{ props.product.item }}</p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul {
    list-style: none;
}
</style>