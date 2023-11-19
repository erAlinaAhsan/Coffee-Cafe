<template>
  <div>
    <div class="container">
      <div class="banner">
        <img :src="imagePath9" />
      </div>
      <div class="list-container" v-if="showListContainer">
        <div
          class="flex-div"
          v-for="coffee in filteredCoffees"
          :key="coffee.id"
          display="flex"
          @click="toggleDetails(coffee)"
        >
          <img :src="coffee.image" class="imgs" />
          <p>
            <b>{{ coffee.title }}</b>
            <br />
          </p>
          <p class="description" v-show="coffee.showDetails">
            {{ coffee.description }}
          </p>
          <p v-show="coffee.showDetails">{{ coffee.ingredients }}</p>
          <p v-show="coffee.showDetails">{{ coffee.id }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainContent",
  props: {
    msg: String,
    coffees: Array,
    imagePath9: String,
    showListContainer: Boolean,
  },
  data() {
    return {
      imageUrll: require("@/assets/background.jpeg"),
    };
  },
  methods: {
    toggleDetails(coffee) {
      // Toggle the showDetails property of the clicked coffee
      coffee.showDetails = !coffee.showDetails;
    },
  },
  computed: {
    filteredCoffees() {
      // Filter coffees based on the showListContainer prop
      return this.showListContainer ? this.coffees : [];
    },
  },
};
</script>



<style scoped>
.container {
  background: #f9f9f9;
  padding-left: 17%;
  padding-right: 2%;
  padding-top: 20px;
  padding-bottom: 20px;
  margin-top: 250px;
  overflow-x: hidden;
}
.banner {
  display: flex;
  width: 100%;
}
.banner img {
  width: 100%;
  height: 60vh;
  border-radius: 8px;
}
.list-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  grid-column-gap: 16px;
  grid-row-gap: 30px;
  margin-top: 50px;
}
.listdesp-container p {
  display: none;
}
.large-container {
  padding-left: 7%;
  overflow-x: hidden;
}
.hidden-container {
  display: none;
}
.flex-div img {
  width: 70%;
  border-radius: 3%;
  margin-right: 10px;
}
.flex-div {
  align-items: flex-start;
  margin-top: 7px;
}
.description {
  color: #5a5a5a;
  font-size: 14px;
}
</style>
