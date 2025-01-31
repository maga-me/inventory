<template>
  <div class="modalCard">

    <button class="modalCard__close">
      <img src="../../assets/images/close-icon.svg" alt="" class="modalCard__close-icon">
    </button>
    <img
      src="../../assets/images/Item-image-green.png"
      alt=""
      class="modalCard__img"
    />

    <span class="modalCard__line"></span>

    <div class="modalCard__skeletons">
      <img src="../../assets/images/Stub.png" alt="" />

      <img src="../../assets/images/Content.png" alt="" />
    </div>

    <span class="modalCard__line"></span>

    <button class="modalCard__button">Удалить предмет</button>
  </div>
</template>

<style lang="scss">
.modalCard {
  position: absolute;
  right: 0;
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

  &__close {
    border: 0;
    outline: none;
    background: transparent;
    padding: 6px;
    position: absolute;
    top: 14px;
    right: 14px;
    cursor: pointer
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
    background: #FA7272;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.2s;

    &:hover {
      background: #FF8888;
    }
  }
}
</style>
