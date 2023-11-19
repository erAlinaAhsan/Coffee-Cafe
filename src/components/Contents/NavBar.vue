<template>
  <nav
    class="flex-div"
    :style="{
      backgroundImage: 'url(' + imageUrl + ')',
    }"
  >
    <img :src="imagePath" class="menu-icon" />
    <div class="nav-middle">
      <div class="search-box">
        <input type="text" placeholder="Looking for something specific?" />
        <img :src="imagePath1" class="search-icon" />
      </div>
    </div>
    <img :src="imagePath2" class="coffeeshop-logo" />
  </nav>
  <nav
    class="flex-div1 btnbtn"
    :style="{
      backgroundImage: 'url(' + imageUrl + ')',
    }"
  >
    <h4 class="btn1" @click="emitAllButtonClick">Our Menu</h4>
    <h4 class="btn2" @click="filterHotCoffee">Hot-Coffee</h4>
    <h4 class="btn3" @click="filterColdCoffee">Cold-Coffee</h4>
    <h4 class="btn4" @click="filterBlackCoffee">Black-Coffee</h4>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  props: {
    imagePath: String,
    imagePath1: String,
    imagePath2: String,
  },
  data() {
    return {
      imageUrl: require("@/assets/navbar.jpeg"),
    };
  },
  methods: {
    emitAllButtonClick() {
      this.$emit("allButtonClick");
    },
    filterHotCoffee() {
      this.$emit("filterHotCoffee");
    },
    filterColdCoffee() {
      this.$emit("filterColdCoffee");
    },
    filterBlackCoffee() {
      this.$emit("filterBlackCoffee");
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
nav.flex-div1 {
  display: flex;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  align-items: center;
  position: absolute;
  justify-content: flex-end;
  margin-top: 60px;
  overflow-x: hidden;
  width: 100%;
}
img.menu-icon {
  cursor: pointer;
  border-radius: 25px;
  height: 40px;
  width: 40px;
  margin-left: 50px;
  align-self: center;
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
  align-self: center;
  border: 1px solid #ccc;
  margin-right: 15px;
  padding: 10px;
  border-radius: 25px;
  margin-top: 10px;
}
.flex-div1 h4 {
  display: flex;
  align-self: auto;
  border: 1px solid #ccc;
  padding: 10px;
  color: #ccc;
  border-radius: 5px;
  margin-right: 200px;
  width: 100px;
  border: 0;
  outline: 0;
  background-color: rgb(73, 43, 43);
  cursor: pointer;
  transition: background-color 0.3s ease;

  /* Center the text within the button */
  display: flex;
  justify-content: center;
  align-items: center;
}
.btn1:hover,
.btn2:hover,
.btn3:hover,
.btn4:hover {
  padding: 12px;
  transition: padding 0.4s ease;
  border-radius: 5px;
  background-color: #ccc;
  color: black;
}

.flex-div1 button:hover {
  background-color: #f0f0f0;
}
button.btn {
  margin-right: 400px;
}

.nav-middle .search-box input {
  width: 400px;
  border: 0;
  outline: 0;
  background: transparent;
}
.flex-div .coffeeshop-logo {
  width: 60px;
}
</style>
