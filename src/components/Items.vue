<template>
    <div class="items">
        <div class="items__container">
            <Item v-for="item in items" :key="item.id" :name="item.name" @click="$emit('select', item)" />
        </div>
    </div>
</template>

<script>
import Item from '@/components/Item.vue';

export default {
    name: 'Items',
    props: ['items'],
    components: {
        Item,
    }
}
</script>

<style>
.items {
    border: 2px solid #000;
    border-radius: 10px;
    padding: 10px 15px;
    width: 40%;
    height: 500px;
}
.items__container {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}
</style>