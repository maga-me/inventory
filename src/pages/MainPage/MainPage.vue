<script setup>
import { ref, watch } from "vue";
import draggable from "vuedraggable";
import ItemVue from "../../components/Item/Item.vue";
import ModalVue from "../../components/Modal/Modal.vue";
const modalItemId = ref(null)
const filteredItem = ref('')
const items = ref([
  { id: 1, path: "Item-image-green.png", amount: 4 },
  { id: 2, path: "Item-image-orange.png", amount: 3 },
  { id: 3, path: "Item-image-purple.png", amount: 2 },
  { id: 4, path: "", amount: 0 },
  { id: 5, path: "", amount: 0 },
  { id: 6, path: "", amount: 0 },
  { id: 7, path: "", amount: 0 },
  { id: 8, path: "", amount: 0 },
  { id: 9, path: "", amount: 0 },
  { id: 10, path: "", amount: 0 },
  { id: 11, path: "", amount: 0 },
  { id: 12, path: "", amount: 0 },
  { id: 13, path: "", amount: 0 },
  { id: 14, path: "", amount: 0 },
  { id: 15, path: "", amount: 0 },
  { id: 16, path: "", amount: 0 },
  { id: 17, path: "", amount: 0 },
  { id: 18, path: "", amount: 0 },
  { id: 19, path: "", amount: 0 },
  { id: 20, path: "", amount: 0 },
  { id: 21, path: "", amount: 0 },
  { id: 22, path: "", amount: 0 },
  { id: 23, path: "", amount: 0 },
  { id: 24, path: "", amount: 0 },
  { id: 25, path: "", amount: 0 },
]); // Your array of items

// Track indexes instead of IDs
const dragState = ref({
  originalIndex: -1,
  newIndex: -1
});

// Handle drag changes
const onDragChange = (event) => {
  if (event.moved) {
    dragState.value = {
      originalIndex: event.moved.oldIndex,
      newIndex: event.moved.newIndex
    };

    for (let i = 0; i < items.length; i++) {
      
    }
    
    console.log("Moved item ID:", items.value[event.moved.newIndex].id);
    console.log("From index:", event.moved.oldIndex, "to:", event.moved.newIndex);
  }
};

const openCloseModal = (itemId) => {
  modalItemId.value = itemId

  filteredItem.value = items.value.find(item => itemId === item.id);
console.log(filteredItem.value);


}

watch(dragState, (newState) => {
  if (newState.originalIndex === -1) return;
  
  const movedItem = items.value[newState.newIndex];
  console.log(`Item ${movedItem.id} moved from 
    position ${newState.originalIndex} to ${newState.newIndex}`);
});
</script>

<template>
  <section class="inventory">
    <div class="container">
      <div class="inventory__card">
        <img
          src="../../assets/images/blurImg.png"
          alt=""
          class="inventory__card-img"
        />
        <img
          src="../../assets/images/skeletons.png"
          alt=""
          class="inventory__card-skeletons"
        />
      </div>

      <div class="inventory__box">
        <draggable
          v-model="items"
          class="inventory__box-row"
          tag="ul"
          name="flip-list"
          :swap-threshold="0.5"
          @change="onDragChange"
          item-key="id"
        >

          <template #item="{ element }">
            <ItemVue :item="element" :modalItemId="modalItemId" @itemIdForModal="openCloseModal" />
          </template>

        </draggable>

        <ModalVue :item="filteredItem"  :class="{active: modalItemId == null ? false : true }" @closeModal="openCloseModal" />

        </div>
      </div>
  </section>

  <footer class="footer">
    <div class="container">
      <div class="footer__skeleton">
        <img
          src="../../assets/images/Skeleton.png"
          alt=""
          class="footer__skeleton-img"
        />

        <button class="footer__skeleton-close">
          <img src="../../assets/images/close-icon.svg" alt="" />
        </button>
      </div>
    </div>
  </footer>
</template>
