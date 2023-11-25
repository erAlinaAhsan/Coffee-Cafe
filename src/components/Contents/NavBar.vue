<template>
  <div>
    <nav class="flex-div">
      <img :src="imagePath" class="menu-icon" />
      <div class="nav-middle">
        <div class="search-box">
          <input
            type="text"
            v-model="searchQuery"
            placeholder="Search by ingredients..."
            @input="handleSearchInput"
          />
          <img :src="imagePath1" class="search-icon" />
        </div>
      </div>
    </nav>
    <nav class="flex-div1">
      <h4
        class="btn"
        :class="{ active: selectedIngredient === '' }"
        @click="emitAllButtonClick"
      >
        All
      </h4>

      <h4
        class="tags"
        v-for="(ingredient, index) in ingredientsList"
        :key="index"
        :class="{ active: selectedIngredient === ingredient }"
        @click="filterByIngredient(ingredient)"
      >
        {{ ingredient }}
      </h4>
    </nav>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  props: {
    imagePath: String,
    imagePath1: String,
    ingredientsList: Array,
  },
  data() {
    return {
      searchQuery: "",
      selectedIngredient: "",
    };
  },
  created() {
    // Set "All" button as active by default
    this.selectedIngredient = "";
  },

  methods: {
    emitAllButtonClick() {
      console.log("Emitting allButtonClick event");
      this.selectedIngredient = "";
      this.$emit("allButtonClick");
    },
    filterByIngredient(ingredient) {
      this.selectedIngredient = ingredient;
      this.$emit("filterByIngredient", ingredient);
    },
    handleSearchInput() {
      // Emit the search query for handling in the parent component
      this.$emit("searchByIngredient", this.searchQuery);
    },
  },
};
</script>

<style scoped>
nav {
  display: flex;

  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  position: absolute;
  width: 100%;
  top: 0;
  z-index: 10;
  padding: 5px;
  align-content: center;
  justify-content: space-between;
  overflow-x: hidden;
  /* background-color: rgba(165, 42, 42, 0.5); */
}
nav.flex-div {
  margin-right: 20px;
  width: 100%;
}
.flex-div1 .active {
  background-color: #969494;
  color: #3b3b3b;
}
nav.flex-div1 {
  display: flex;
  /* flex-wrap: wrap; */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  align-items: center;

  /* position: absolute; */
  justify-content: space-evenly;
  margin-top: 55px;
  /* margin-left: 100px; */
  /* overflow-x: hidden; */
  overflow: scroll;
  /* width: 100%; */
}
::-webkit-scrollbar {
  width: 8px;
  height: 5px;
}

::-webkit-scrollbar-thumb {
  background-color: #a0a0a0; /* Thumb color */
  border-radius: 4px; /* Round the corners of the thumb */
}

::-webkit-scrollbar-track {
  background-color: #f0f0f0; /* Track color */
}

img.menu-icon {
  cursor: pointer;
  border-radius: 25px;
  height: 40px;
  width: 40px;
  margin-left: 30px;
  align-self: center;
  margin-top: 15px;
}
img.search-icon {
  width: 15px;
  /* margin-top: 5px; */
}
img.coffeeshop-logo {
  margin-right: 150px;
}
.nav-middle .search-box {
  display: flex;
  justify-content: space-around;
  align-self: center;
  border: 1px solid #565656;
  margin-right: 600px;
  padding: 10px;
  border-radius: 25px;
  margin-top: 15px;
}
.btn,
.tags {
  display: flex;
  justify-content: flex-start;
  align-self: center;
  border: 1px solid #ccc;
  padding: 10px;
  color: #9e9e9e;
  border-radius: 5px;
  width: fit-content;

  border: 0;
  outline: 0;
  font-size: 14px;
  background-color: rgb(26, 25, 25);
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-right: 10px;
}
.btn:first-child,
.tags:first-child {
  margin-left: 540px;
}

h4:hover {
  /* padding: 12px; */
  /* transition: padding 0.4s ease; */
  /* border-radius: 5px; */
  background-color: rgb(48, 47, 47);
  /* color: black; */
}

.flex-div1 button:hover {
  background-color: #f0f0f0;
}

.nav-middle .search-box input {
  width: 400px;
  border: 0;
  border-color: #565656;
  outline: 0;
  background: transparent;
  color: white;
}
.flex-div .coffeeshop-logo {
  width: 60px;
}
@media (max-width: 900px) {
  .nav-middle .search-box input {
    width: 300px;
  }
  .menu-icon {
    margin-right: 30px;
  }
  .btn:first-child,
  .tags:first-child {
    margin-right: 790px;
  }
}
</style>
