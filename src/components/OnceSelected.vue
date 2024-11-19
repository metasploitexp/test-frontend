<template>
    <div class="once-selected" @click="handleClick">
        {{ name }}
    </div>
</template>

<script>
export default {
    name: 'OnceSelected',
    props: ['item'],
    computed: {
        name() {
            return this.item?.name || 'SELECTED ITEM'
        }
    },
    methods: {
        handleClick() {
            if (this.item) {
                this.$emit('unselect', this.item)
            }
        }
    }
}
</script>

<style>
.once-selected {
    font-size: 32px;
    border: 2px solid #000;
    border-radius: 10px;
    width: 300px;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    user-select: none;
}
</style>