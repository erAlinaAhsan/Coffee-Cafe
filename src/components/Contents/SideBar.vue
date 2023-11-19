<template>
  <div class="sidebar">
    <div class="shortcut-links">
      <a href=""
        ><img :src="imagePath3" />
        <p>Home</p></a
      >
      <a href=""
        ><img :src="imagePath4" />
        <p>About Us</p></a
      >
      <a href=""
        ><img :src="imagePath5" />
        <p>Coffee Club</p></a
      >
      <a href=""
        ><img :src="imagePath6" />
        <p>Order Online</p></a
      >
      <a href=""
        ><img :src="imagePath8" />
        <p>Behind the Beans</p></a
      >
      <a href=""
        ><img :src="imagePath7" />
        <p>Store Locator</p></a
      >
      <hr />
    </div>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  props: {
    imagePath3: String,
    imagePath4: String,
    imagePath5: String,
    imagePath6: String,
    imagePath7: String,
    imagePath8: String,
  },
};
</script>

<style scoped>
.sidebar {
  background: #fff;
  width: 15%;
  height: 100vh;
  position: fixed;
  top: 0;
  padding-left: 2%;
  padding-top: 80px;
}
.shortcut-links a img {
  width: 40px;
  margin-right: 20px;
}
.shortcut-links a {
  display: flex;
  align-items: center;
  margin-bottom: 30px;
  margin-top: 60px;
  width: fit-content;
  flex-wrap: wrap;
  color: rgb(64, 64, 64);
  text-decoration: none;
}
.shortcut-links a:first-child {
  color: #ed3833;
}
.sidebar hr {
  border: 0;
  height: 1px;
  background: #ccc;
  width: 85%;
}
.small-sidebar {
  width: 5%;
}
.small-sidebar a p {
  display: none;
}
.small-sidebar h3 {
  display: none;
}
.small-sidebar hr {
  width: 50%;
  margin-bottom: 25px;
}
</style>
