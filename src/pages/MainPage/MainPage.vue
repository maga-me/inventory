<script setup>
import { ref, watch } from "vue";
import draggable from "vuedraggable";

const drag = ref(false);
const draggedItem = ref(null); // Track the dragged item

const items = ref([
  { id: 1, path: "../../assets/images/Item-image-green.png" },
  { id: 2, path: "../../assets/images/Item-image-orange.png" },
  { id: 3, path: "../../assets/images/Item-image-purple.png" },
  { id: 4, path: "" },
  { id: 5, path: "" },
  { id: 6, path: "" },
  { id: 7, path: "" },
  { id: 8, path: "" },
  { id: 9, path: "" },
  { id: 10, path: "" },
  { id: 11, path: "" },
  { id: 12, path: "" },
  { id: 13, path: "" },
  { id: 14, path: "" },
  { id: 15, path: "" },
  { id: 16, path: "" },
  { id: 17, path: "" },
  { id: 18, path: "" },
  { id: 19, path: "" },
  { id: 20, path: "" },
  { id: 21, path: "" },
  { id: 22, path: "" },
  { id: 23, path: "" },
  { id: 24, path: "" },
  { id: 25, path: "" },
]);

const onDragStart = (event) => {
  draggedItem.value = event.item.id; // Track the dragged item ID
};

const onDragEnd = () => {
    console.log("asdasd");
};

// Deep watcher to capture changes in order
watch(
  items,
  (newItems) => {
    console.log("Watcher triggered. Updated positions:", newItems);
  }
);
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
          @start="onDragStart"
          @end="onDragEnd"
          item-key="id"
        >
          <template #item="{ element }">
            <li
              class="inventory__box-item"
            >
            <img :src="`${element?.path}`" v-show="element?.path" alt="asd" class="inventory__box-item--img">
            </li>
          </template>
        </draggable>
      </div>
    </div>
  </section>

  <footer class="footer">
    <div class="container">
      <div class="footer__skeleton"></div>
    </div>
  </footer>
</template>
