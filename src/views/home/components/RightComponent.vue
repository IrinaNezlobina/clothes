<template>
  <div class="grid gap-3">
    <div
      class="m-4 ml-auto selected-item rounded-md w-40 h-40 flex items-center justify-center
      text-lg p-3 border border-gray:50 inline-block">
      <p v-if="selectedItem">{{ selectedItem.name }}</p>
      <p v-else>Выберите элемент</p>
    </div>
    <div class="grid gap-3 grid-cols-2 rounded-md  p-3 border border-gray:50">
      <div
        v-for="(item, index) in userStuff"
        :key="index"
        @click="selectItem(item)"
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
    const selectedItem = ref(null);

    const userStuff = ref([
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
    ]);
    // methods
    const selectItem = (item) => {
      selectedItem.value = item;
    };
    return {
      selectedItem,
      selectItem,
      userStuff
    };
  },
});
</script>
