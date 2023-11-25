<template>
  <div class="sidebar small-sidebar">
    <div class="shortcut-links">
      <a href=""> <p>Home</p></a>
      <a href=""> <p>About Us</p></a>
      <a href=""> <p>Coffee Club</p></a>
      <a href=""> <p>Order Online</p></a>
      <a href=""> <p>Behind the Beans</p></a>
      <a href=""> <p>Store Locator</p></a>
      <hr />
    </div>
  </div>
</template>

<script>
export default {
  name: "SideBar",
};
</script>

<style scoped>
.sidebar {
  display: flex;
  width: 15%;
  height: 100vh;
  position: absolute;
  top: 0;
  margin-top: 120px;
  padding-left: 2%;
  padding-top: 80px;
}
/* .shortcut-links a img {
  width: 40px;
  margin-right: 20px;
} */
.shortcut-links a {
  display: flex;
  justify-content: flex-start;
  margin-top: 10px;
  width: fit-content;
  color: #9e9e9e;
  text-decoration: none;
}
.shortcut-links a:first-child {
  color: #ed3833;
}
.sidebar hr {
  border: 0;
  height: 1px;
  background: #ccc;
  width: 90%;
  margin-right: 70px;
}
.small-sidebar {
  width: 5%;
}
.small-sidebar img {
  display: none;
}
.small-sidebar a p {
  display: none;
}
.small-sidebar h3 {
  display: none;
}
.small-sidebar hr {
  display: none;
  width: 50%;
  margin-bottom: 25px;
}
@media (max-width: 900px) {
  .sidebar {
    width: 15%;
  }
  .shortcut-links p {
    align-self: flex-start;
  }
}
</style>
