<template>
  <div class="imgWrapper">
    <div class="imgWrapper__item">
      <img :src="img" alt="random image of a dog" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Image",
  props: {
    img: {
      img: String,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.imgWrapper {
  width: 100%;
  height: auto;
  cursor: pointer;

  &__item {
    height: 160px;
    overflow: hidden;
  }

  img {
    display: block;
    max-width: 100%;
    transition: all 0.3s ease;

    &:hover {
      transform: scale(1.1);
    }
  }
}
</style>
