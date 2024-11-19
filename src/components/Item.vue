<template>
    <div class="item">
        {{ name }}
    </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['name']
}
</script>

<style>
.item {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 5px 10px;
    border: 1px solid #000;
    border-radius: 5px;
    cursor: pointer;
    width: fit-content;
    height: fit-content;
    user-select: none;
}
</style>