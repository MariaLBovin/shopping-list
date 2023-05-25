<script setup lang="ts">
import { ref } from "vue";
// import {IShoppingList} from "../models/IShoppingList";
// const shoppingList = ref<IShoppingList []>([]);
const shoppingItem = ref("");
const itemCategory = ref("")

const emits = defineEmits<{ (e: 'addItem', item: string, category: string, inBasket: boolean) : void}>()

const handleSubmit  = () => {
     emits('addItem', shoppingItem.value, itemCategory.value, false)
    shoppingItem.value = "";
    itemCategory.value = "";
    
}
</script>

<template>
<form @submit.prevent="handleSubmit">
    <input v-model="shoppingItem" type="text" placeholder="Att handla">
    <select v-model="itemCategory" >
        <option>Mejeri</option>
        <option>Skafferi</option>
        <option>Grönsaker och frukt</option>
        <option>Hygien och städ</option>
    </select>
    <button>Spara</button>
</form>
    
</template>

<style scoped>

</style>