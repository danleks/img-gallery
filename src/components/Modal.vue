<template>
  <div class="modalWrapper">
    <div class="modalWrapper__inner">
      <img :src="item" />
      <div @click="$emit('close-modal');" class="modalWrapper__close"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: String,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.modalWrapper {
  position: absolute;
  top: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.9);

  // @media (min-width: 1024px) {
  //     height: 100%;
  //   }

  &__inner {
    position: relative;
    width: 100%;
    height: 100vh;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;

    @media (min-width: 1024px) {
      width: 80%;
      height: 70%;
    }

    img {
      display: block;
      max-width: 90%;

      @media (min-width: 1024px) {
        max-height: 70%;
      }
    }
  }

  &__close {
    width: 40px;
    height: 20px;
    position: absolute;
    right: 35px;
    top: 20px;
    cursor: pointer;

    &::before,
    &::after {
      position: absolute;
      top: 8px;
      left: 10px;
      content: "";
      width: 18px;
      height: 3px;
      background-color: black;
    }

    &::before {
      transform: rotate(45deg);
    }

    &::after {
      transform: rotate(-45deg);
    }
  }
}
</style>
