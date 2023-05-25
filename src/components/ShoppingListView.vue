<script setup lang="ts">
import {IShoppingList} from "../models/IShoppingList";

interface IShoppingListProps {
    product : IShoppingList
}

const props = defineProps<IShoppingListProps>();

</script>

<template>
<div>
        <ul>
            <li :class="{'dairy': props.product.category === 'Mejeri', 
            'pantry': props.product.category === 'Skafferi', 
            'fruit': props.product.category === 'Grönsaker och frukt', 
            'cleaning': props.product.category === 'Hygien och städ',
            'inBasket': props.product.inBasket}"
            >
                <p>Produkt: {{ props.product.item }}</p>
                <p>Kategori: {{ props.product.category }}</p>
                <label name="checkbox">Lägg i korgen</label>
                <input @change="$emit('addToBasket', props.product)" type="checkbox" :checked="props.product.inBasket">
            </li>
        </ul>
    </div>
</template>

<style scoped>
ul {
    list-style: none;
}
.dairy {
    color: blue;
}
.pantry {
    color: brown;
}
.fruit {
    color: red;
}
.cleaning {
    color: black;
}
.inBasket {
    text-decoration: line-through;
}
</style>