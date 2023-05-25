<script setup lang="ts">
import { ref } from 'vue';
import {IShoppingList} from "../models/IShoppingList";
import ShoppingListForm from './ShoppingListForm.vue';
import ShoppingListView from './ShoppingListView.vue';
import BasketList from './BasketList.vue'

const shoppingList = ref<IShoppingList []>([]);

const itemsInBasket = ref<IShoppingList []>([]);


const addItem = (item: string, category: string, inBasket: boolean) => {
    //console.log(item, category, inBasket, );
    const newItem = ({item, category, inBasket});

    shoppingList.value.push(newItem)
    
}

const addToBasket = (product: IShoppingList) => {
    product.inBasket = true;
    itemsInBasket.value.push(product)
}

</script>

<template>
    <ShoppingListForm @addItem="addItem"/>
    <h2>Varor i listan</h2>
    <ShoppingListView 
    v-for="product in shoppingList" 
    :product="product"
    @addToBasket = "addToBasket"
    />
    <h2>Varor i korgen:</h2>
    <BasketList 
    v-for="product in itemsInBasket"
    :product = "product"
     />

</template>

<style scoped>

</style>