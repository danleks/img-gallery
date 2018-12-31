<template>
  <div id="app">
    <h1>Responsive gallery with vue</h1>
    <div v-if="modalOpen === false" class="content">
      <app-image
        :img="img"
        v-for="img in imgArray"
        :key="img"
        @click.native="handleModalOpen(img);"
      />
    </div>

    <app-modal
      :item="modalItem"
      v-if="modalOpen"
      @close-modal="modalOpen = false;"
    />
  </div>
</template>

<script>
import axios from "axios";
import Image from "./components/Image.vue";
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  data() {
    return {
      imgArray: "",
      modalItem: null,
      modalOpen: false
    };
  },

  components: {
    "app-image": Image,
    "app-modal": Modal
  },

  methods: {
    handleModalOpen(item) {
      this.modalItem = item;
      this.modalOpen = true;
    },
    getRandomCat() {
      axios
        .get("https://dog.ceo/api/breeds/image/random/12")
        .then(response => {
          this.imgArray = response.data.message;
        })
        .catch(error => {
          console.log(error);
        });
    }
  },

  created() {
    this.getRandomCat();
  }
};
</script>

<style lang="scss">
body {
  background-color: #e9fdfc;
}

#app {
  position: relative;

  width: 80%;
  height: 100%;
  margin: auto;
  //padding: 20px;
  background-color: #fff;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

*,
*::before,
*::after {
  padding: 0;
  margin: 0;
}

h1 {
  padding: 20px 0;
  font-size: 18px;

  @media (min-width: 768px) {
    font-size: 40px;
    line-height: 2;
  }

  @media (min-width: 1024px) {
    font-size: 40px;
    line-height: 2;
  }
}

.content {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 20px;

  @media (min-width: 768px) {
    grid-template-columns: 1fr 1fr;
  }

  @media (min-width: 1024px) {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>
