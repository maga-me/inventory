<script setup>
import { ref } from "vue";

const delOpt = ref(false);

const props = defineProps({
  item: {
    type: Object,
    required: true,
  }
});

const openOptions = (com) => {
  if(com == 'open') {
    delOpt.value = true;
    
  } else if(com == 'close') {
    delOpt.value = false;
  }

};
</script>

<template>
  <div class="modalCard">
    <button class="modalCard__close" @click="$emit('closeModal', null)">
      <img
        src="../../assets/images/close-icon.svg"
        alt=""
        class="modalCard__close-icon"
      />
    </button>
    <img
      :src="`src/assets/images/${item.path}`"
      alt=""
      class="modalCard__img"
    />

    <span class="modalCard__line"></span>

    <div class="modalCard__skeletons">
      <img src="../../assets/images/Stub.png" alt="" />

      <img src="../../assets/images/Content.png" alt="" />
    </div>

    <span class="modalCard__line"></span>

    <button class="modalCard__button" @click="openOptions('open')">
      Удалить предмет
    </button>

    <div class="modalCard__delOpt" :class="{active: delOpt}">
      <input type="number" name="" id="" placeholder="Введите количество" class="modalCard__delOpt-inp" />

      <div class="modalCard__delOpt-btns">
        <button class="modalCard__delOpt-btn cancel" @click="openOptions('close')">Отмена</button>
        <button class="modalCard__delOpt-btn accept">Подтвердить</button>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.modalCard {
  position: absolute;
  right: -100%;
  top: 0;
  height: calc(100% - 2px);
  background: #26262680;
  backdrop-filter: blur(16px);
  width: calc(50% - 25px);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 65px 18px 15px;
  border-radius: 0 12px 12px 0;
  border: 1px solid #4d4d4d;
  justify-content: space-between;
  transition: 0.4s;

  &.active {
    right: 0;
  }

  &__close {
    border: 0;
    outline: none;
    background: transparent;
    padding: 6px;
    position: absolute;
    top: 14px;
    right: 14px;
    cursor: pointer;
  }

  &__img {
    max-width: 130px;
    width: 100%;
    height: 130px;
    margin-bottom: 55px;
  }

  &__line {
    height: 1px;
    width: 100%;
    background: #4d4d4d;

    &:nth-of-type(1) {
      margin-bottom: 30px;
    }
    &:nth-of-type(2) {
      margin: 55px 0 30px;
    }
  }

  &__skeletons {
    width: 100%;
    animation: skeleton 2s infinite;

    img {
      width: 100%;
      &:nth-of-type(1) {
        margin-bottom: 30px;
      }
    }
  }

  &__button {
    border: 0;
    width: 100%;
    padding: 11px 55px;
    color: #fff;
    background: #fa7272;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.2s;

    &:hover {
      background: #ff8888;
    }
  }

  &__delOpt {
    padding: 20px 22px;
    position: absolute;
    bottom: -100%;
    width: 100%;
    border: 1px solid #4d4d4d;
    background: #26262699;
    backdrop-filter: blur(16px);
    min-height: 140px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 30px;
    transition: 0.4s;
    
    &.active {
      bottom: 0;
      transition: 0.4s;
    }

    &-inp,
    &-btns {
      width: 100%;
    }

    &-btns {
      display: flex;
      flex-direction: row;
      gap: 10px;
      justify-content: space-between;
    }

    &-inp {
      padding: 12px;
      border: 1px solid #4d4d4d;
      border-radius: 4px;
      background: #262626;
      color: #fff;
    }
    
    &-btn {
      border: 0;
      cursor: pointer;
      border-radius: 8px;
      padding: 8px 20px;
      width: 40%;
      transition: 0.2s;

      &:nth-of-type(2) {
        background: #FA7272;
        color: #fff;
        width: 60%;
        
        &:hover {
          background: #FF8888;
        }
      }
    }
  }
}
</style>
