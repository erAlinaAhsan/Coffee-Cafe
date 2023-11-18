<template>
  <div>
    <NavBar
      :imagePath="imagePath"
      :imagePath1="imagePath1"
      :imagePath2="imagePath2"
      @allButtonClick="toggleListContainer"
      @filterHotCoffee="filterHotCoffee"
      @filterColdCoffee="filterColdCoffee"
      @filterBlackCoffee="filterBlackCoffee"
    />
    <SideBar
      :imagePath3="imagePath3"
      :imagePath4="imagePath4"
      :imagePath5="imagePath5"
      :imagePath6="imagePath6"
      :imagePath7="imagePath7"
      :imagePath8="imagePath8"
    />
    <MainContent
      :msg="msg"
      :coffees="coffees"
      :imagePath9="imagePath9"
      :showListContainer="showListContainer"
    />
  </div>
</template>

<script>
import NavBar from "@/components/Contents/NavBar.vue";
import SideBar from "@/components/Contents/SideBar.vue";
import MainContent from "@/components/Contents/MainContent.vue";

export default {
  name: "CoffeeShop",
  components: {
    NavBar,
    SideBar,
    MainContent,
  },
  data() {
    return {
      imagePath: require("@/assets/bars.png"),
      imagePath1: require("@/assets/search-icon.png"),
      imagePath2: require("@/assets/coffee-shop-logo.jpeg"),
      imagePath3: require("@/assets/home.png"),
      imagePath4: require("@/assets/about-us.png"),
      imagePath5: require("@/assets/menu.png"),
      imagePath6: require("@/assets/franchise.webp"),
      imagePath7: require("@/assets/contact.png"),
      imagePath8: require("@/assets/messages.webp"),
      imagePath9: require("@/assets/banner.webp"),
      coffees: [],
      showListContainer: false,
      hotCoffeeClicked: false,
      coldCoffeeClicked: false,
      blackCoffeeClicked: false,
    };
  },
  methods: {
    toggleListContainer() {
      this.showListContainer = !this.showListContainer;
      if (this.showListContainer) {
        // Fetch the coffee data again when "All" or "Hot-Coffee" button is clicked
        fetch("https://api.sampleapis.com/coffee/hot")
          .then((response) => response.json())
          .then((alina) => {
            this.coffees = alina.map((coffee) => ({
              ...coffee,
              showDetails: false,
            }));
          })
          .catch((error) => {
            console.error("Error fetching data:", error);
          });
      }
    },

    async filterHotCoffee() {
      this.hotCoffeeClicked = true;
      this.showListContainer = !this.showListContainer;
      const specificCoffeeIds = [2, 3, 4, 6, 7, 8, 9, 10, 11];
      const coffeeData = await fetch("https://api.sampleapis.com/coffee/hot")
        .then((response) => response.json())
        .then((alina) => {
          return alina.filter((coffee) =>
            specificCoffeeIds.includes(coffee.id)
          );
        })
        .catch((error) => {
          console.error("Error fetching data:", error);
          return [];
        });

      this.coffees = coffeeData.map((coffee) => ({
        ...coffee,
        showDetails: false,
      }));
    },

    async filterColdCoffee() {
      this.coldCoffeeClicked = true;
      this.showListContainer = !this.showListContainer;
      const specificCoffeeIds = [14, 15, 16, 17, 18, 19, 20];
      const coffeeData = await fetch("https://api.sampleapis.com/coffee/hot")
        .then((response) => response.json())
        .then((alina) => {
          return alina.filter((coffee) =>
            specificCoffeeIds.includes(coffee.id)
          );
        })
        .catch((error) => {
          console.error("Error fetching data:", error);
          return [];
        });

      this.coffees = coffeeData.map((coffee) => ({
        ...coffee,
        showDetails: false,
      }));
    },

    async filterBlackCoffee() {
      this.blackCoffeeClicked = true;
      this.showListContainer = !this.showListContainer;
      const specificCoffeeIds = [1, 5, 12, 13];
      const coffeeData = await fetch("https://api.sampleapis.com/coffee/hot")
        .then((response) => response.json())
        .then((alina) => {
          return alina.filter((coffee) =>
            specificCoffeeIds.includes(coffee.id)
          );
        })
        .catch((error) => {
          console.error("Error fetching data:", error);
          return [];
        });

      this.coffees = coffeeData.map((coffee) => ({
        ...coffee,
        showDetails: false,
      }));
    },
  },
  created() {
    fetch("https://api.sampleapis.com/coffee/hot")
      .then((response) => response.json())
      .then((alina) => {
        this.coffees = alina.map((coffee) => ({
          ...coffee,
          showDetails: false,
        }));
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
      });
  },
  mounted() {
    var menuIcon = document.querySelector(".menu-icon");
    var btnbtn = document.querySelector(".btnbtn");
    var sidebar = document.querySelector(".sidebar");
    var container = document.querySelector(".container");
    var banner = document.querySelector(".banner");
    var imgsList = document.querySelectorAll(".imgs");
    var listcontainer = document.querySelector(".list-container");

    menuIcon.onclick = function () {
      sidebar.classList.toggle("small-sidebar");
      container.classList.toggle("large-container");
    };
    btnbtn.onclick = function () {
      banner.classList.toggle("hidden-container");
    };
    imgsList.forEach((img) => {
      img.onclick = function () {
        listcontainer.classList.toggle("listdesp-container");
      };
    });
  },
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
  font-family: "poppins", sans-serif;
  box-sizing: border-box;
}
body {
  overflow-y: scroll;
  box-sizing: border-box;
}

body::-webkit-scrollbar {
  width: 5px;
}

body::-webkit-scrollbar-thumb {
  background: #7e7e7e;
  border-radius: 50px;
}
@media (max-width: 900px) {
  .menu-icon {
    display: none;
  }
  .sidebar {
    display: none;
  }
  .container,
  .large-container {
    padding-left: 5%;
    padding-right: 5%;
    overflow-x: hidden;
  }
  nav img {
    display: none;
  }

  .nav-middle .search-box input {
    width: 100%;
  }
  .nav-middle .search-icon {
    display: none;
  }
  .coffeeshop-logo {
    width: 90px;
  }
}
</style>
