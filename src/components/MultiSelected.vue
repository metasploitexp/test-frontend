<template>
    <div class="multi-selected">
        <div class="multi-selected__list">
            <Item v-for="item in items" :key="item.id" :name="item.name" @click="$emit('unselect', item)" />
        </div>
        <div class="multi-selected__counter">
            selected: {{ items.length }} / 6
        </div>
    </div>
</template>

<script>
import Item from '@/components/Item.vue';

export default {
    name: 'MultiSelected',
    props: ['items'],
    components: {
        Item
    }
}
</script>

<style>
.multi-selected {
    width: 300px;
    height: 200px;
    border: 2px solid #000;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 10px;
    padding: 10px 15px;
    overflow-y: auto;
}
.multi-selected__list {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}
.multi-selected__counter {
    text-align: center;
}
</style>