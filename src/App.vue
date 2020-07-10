
<template>
  <div id="app">
    <!-- add Button -->
    <span @click="isShownAddingItemForm = true" class="btn">Добавить</span>
    <AddItem v-if="isShownAddingItemForm" @saveInfo="saveInfo" v-bind:items="items"/>
    <div>
      <!-- general wrapper -->
      <div class="wrapper flexBox">
        <div @click="sortName" class="nameRow flexBox">Имя</div>
        <div @click="sortPhone" class="phoneRow flexBox">Телефон</div>
      </div>
      <!-- add Item components -->
      <Item v-for="dataItem of items" v-bind:dataItem="dataItem" />
    </div>
  </div>
</template>

<script>
import AddItem from "./components/AddItem";
import Item from "./components/Item";

export default {
  name: "App",

  components: {
    Item,
    AddItem
  },
  // add state
  data() {
    return {
      items: [],
      isShownAddingItemForm: false
    };
  },
  // localstarage
  created() {
    if (localStorage.getItem("items")) {
      this.items = JSON.parse(localStorage.getItem("items"));
    }
  },

  methods: {
    // save function
    saveInfo(info) {
      this.items.push(info);
      localStorage.setItem("items", JSON.stringify(this.items));
      this.isShownAddingItemForm = false;
    },
    // sort function by name
    sortName() {
      this.items.sort((a, b) => (a.name > b.name ? 1 : -1));
    },
    // sort function by phone number
    sortPhone() {
      this.items.sort((a, b) => (a.phone < b.phone ? 1 : -1));
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* button styles */
.btn {
  display: block;
  width: 120px;
  height: 20px;
  margin: 20px 50%;
  background: #e4dfdf;
  border: 1px solid black;
  border-radius: 20px;
  cursor: pointer;
}
/* add flex  */
.flexBox {
  display: flex;
  justify-content: start;
}
/* wrapper styles  */
.wrapper {
  width: 60%;
  border: 1px black solid;
}
/* name and phone styles */
.nameRow {
  width: 40%;
  padding: 10px;
  border-right: 1px black solid;
  font-weight: bold;
  cursor: pointer;
}
.phoneRow {
  width: 60%;
  padding: 10px;
  font-weight: bold;
  cursor: pointer;
}
</style>
