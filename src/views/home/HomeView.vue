<template>
  <div>
    <div class="grid gap-3">
      <div
        class="cursor-pointer selected-item">
        <p v-if="selectedItem">{{ selectedItem.name }}</p>
        <p v-else>Выберите элемент</p>
      </div>
      <div class="">
      <div
        v-for="(item, index) in userStuff"
        :key="index"
        @click="selectItem(item)"
        class="">
        {{ item.name }}
      </div>
      </div>
    </div>
    44444444444444
    <div class="grid gap-3">
      <div class="cursor-pointer selected-items">
<!--        <p v-if="selectedItems.length > 0">Выбранные элементы:</p>-->
        <div v-for="(item, index) in selectedItems" :key="index">
          {{ item.name }}
        </div>
<!--        <p v-else>Выберите элементы</p>-->
      </div>
      <div class="">
        <div
          v-for="(item, index) in chooseStuff"
          :key="index"
          @click="selectMultipleItems(item)"
          class="">
          {{ item.name }}
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import { defineComponent,ref, onMounted } from 'vue';


export default defineComponent({
  setup() {
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

    const selectedItem = ref(null);

    const selectedItems = ref([])

    // methods

    const selectItem = (item) => {
      selectedItem.value = item;
    };
    const selectMultipleItems = (item) => {
      // Проверяем, если элемент уже выбран
      const index = selectedItems.value.findIndex(selected => selected.id === item.id);
      if (index === -1) {
        // Если элемент не выбран и количество выбранных элементов меньше 6
        if (selectedItems.value.length < 6) {
          selectedItems.value.push(item); // Добавляем элемент
        } else {
          alert("Вы можете выбрать не более 6 элементов."); // Сообщение об ошибке
        }
      } else {
        // Если элемент уже выбран, удаляем его
        selectedItems.value.splice(index, 1);
      }
    };
    // hooks
    onMounted(async () => {

    });

    return {
      userStuff,
      chooseStuff,
      selectedItem,
      selectItem,
      selectedItems,
      selectMultipleItems
    };
  },
  components: {

  },
});
</script>
