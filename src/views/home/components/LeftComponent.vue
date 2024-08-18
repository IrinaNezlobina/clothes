<template>
  <div class="grid gap-3">
    <div class="grid gap-3 grid-cols-3 m-4 selected-item rounded-md  flex items-center justify-center
      text-lg p-3 border border-gray:50 inline-block selected-items">
      <div
        v-for="(item, index) in selectedItems"
        :key="index"
        class="cursor-pointer mb-4 selected-item rounded-md  p-3 border border-gray:50 hover:bg-blue-400 ">
        {{ item.name }}
      </div>
    </div>
    <div class="mt-auto grid gap-3 grid-cols-2 rounded-md  p-3 border border-gray:50">
      <div
        v-for="(item, index) in chooseStuff"
        :key="index"
        @click="selectMultipleItems(item)"
        class="cursor-pointer mb-4 selected-item rounded-md  p-3 border border-gray:50 hover:bg-blue-400 ">
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    // data
    const chooseStuff = ref([
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
    ]);

    const selectedItems = ref([])

    // methods

    const selectMultipleItems = (item) => {
      const index = selectedItems.value.findIndex(selected => selected.id === item.id);
      if (index === -1) {
        if (selectedItems.value.length < 6) {
          selectedItems.value.push(item);
        } else {
          alert("Вы можете выбрать не более 6 элементов.");
        }
      } else {
        selectedItems.value.splice(index, 1);
      }
    };
    return {
      chooseStuff,
      selectedItems,
      selectMultipleItems
    };
  },
});
</script>

