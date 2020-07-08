<template>
  <div id="app">
    <span @click="addItem = true" class="btn">Добавить</span>
    <AddItem v-if="addItem" @saveInfo="saveInfo" />
    <div>
      <div class="wrapper flexBox">
        <div @click="sortName" class="nameRow flexBox">Имя</div>
        <div @click="sortPhone" class="phoneRow flexBox">Телефон</div>
      </div>
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

  data() {
    return {
      items: [],
      addItem: false,
      sortParam: ""
    };
  },

  created() {
    if (localStorage.getItem("items")) {
      this.items = JSON.parse(localStorage.getItem("items"));
    }
  },

  methods: {
    saveInfo(info) {
      this.items.push(info);
      if (localStorage.getItem("items")) {
        const infoArr = JSON.parse(localStorage.getItem("items"));
        infoArr.push(info);
        localStorage.setItem("items", JSON.stringify(infoArr));
      } else {
        localStorage.setItem("items", JSON.stringify(this.items));
      }
      this.addItem = false;
    },
    sortName() {
      this.items.sort((a, b) => (a > b ? 1 : -1));
    },
    sortPhone() {
      this.items.sort((a, b) => (a < b ? 1 : -1));
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
.flexBox {
  display: flex;
  justify-content: start;
}
.wrapper {
  width: 60%;
  border: 1px black solid;
}
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
