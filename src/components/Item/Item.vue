<script setup>
import { ref } from "vue";

const props = defineProps({
  item: {
    type: Object,
    required: true,
  },
  modalItemId: {
    type: Number,
    required: true
  }
});

const isClicked = ref(false);

const clickedItem = (el) => {
  
    isClicked.value = true;

    const cards = document.querySelectorAll('.inventory__box-item');
    
    cards.forEach(cardd => {
      cardd.classList.remove('active');
    });
};

</script>

<template>
  <li
    class="inventory__box-item"
    :class="{ active: isClicked }"
    @click="clickedItem(item), $emit('itemIdForModal', item.id)"
  >
    <img
      :src="`src/assets/images/${item?.path}`"
      v-show="item?.path"
      alt="asd"
      class="inventory__box-item--img"
    />

    <span class="inventory__box-item--counter">{{ item?.amount }}</span>
  </li>
</template>
