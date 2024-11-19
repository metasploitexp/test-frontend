<template>
  <div class="main">
    <div class="main__selected">
      <MultiSelected :items="userSelectedItems" @unselect="handleMultiUnselect" />
      <OnceSelected :item="otherSelectedItem" @unselect="handleOnceUnselect" />
    </div>
    <div class="main__lists">
      <items :items="userItems" @select="handleMultiSelect" />
      <items :items="otherItems" @select="handleOnceSelect" />
    </div>
  </div>
</template>

<script>
import Items from '@/components/Items.vue';
import MultiSelected from '@/components/MultiSelected.vue';
import OnceSelected from '@/components/OnceSelected.vue';

export default {
  components: {
    Items,
    MultiSelected,
    OnceSelected,
  },
  data() {
    return {
      userItems: [
        {
            "id": 1,
            "name": "Shoes 1"
        },
        {
            "id": 2,
            "name": "Shoes 2"
        },
        {
            "id": 3,
            "name": "Shoes 3"
        },
        {
            "id": 4,
            "name": "Shoes 4"
        },
        {
            "id": 5,
            "name": "T-shirt 1"
        },
        {
            "id": 6,
            "name": "T-shirt 2"
        },
        {
            "id": 7,
            "name": "T-shirt 3"
        },
        {
            "id": 8,
            "name": "T-shirt 4"
        }
      ],
      otherItems: [
        {
            "id": 11,
            "name": "Jacket 1"
        },
        {
            "id": 12,
            "name": "Jacket 2"
        },
        {
            "id": 13,
            "name": "Jacket 3"
        },
        {
            "id": 14,
            "name": "Jacket 4"
        },
        {
            "id": 15,
            "name": "Hoodie 1"
        },
        {
            "id": 16,
            "name": "Hoodie 2"
        },
        {
            "id": 17,
            "name": "Hoodie 3"
        },
        {
            "id": 18,
            "name": "Hoodie 4"
        }
      ],
      userSelectedItems: [],
      otherSelectedItem: null,
    }
  },
  methods: {
    handleMultiSelect(item) {
      if (this.userSelectedItems.length > 5) {
        return
      }

      this.userSelectedItems.push(item)
      this.userItems = this.userItems.filter(x => x.id !== item.id)
    },
    handleOnceSelect(item) {
      if (this.otherSelectedItem) {
        this.otherItems.push(this.otherSelectedItem)
      }
      this.otherSelectedItem = item
      this.otherItems = this.otherItems.filter(x => x.id !== item.id)
    },
    handleMultiUnselect(item) {
      this.userItems.push(item)
      this.userSelectedItems = this.userSelectedItems.filter(x => x.id !== item.id) 
    },
    handleOnceUnselect(item) {
      this.otherItems.push(item)
      this.otherSelectedItem = null
    }
  }
}
</script>

<style>
.main {
  padding: 15px 20px;
  display: flex;
  flex-flow: column;
  gap: 20px;
}

.main__lists, .main__selected {
  display: flex;
  justify-content: space-between;
}
</style>
