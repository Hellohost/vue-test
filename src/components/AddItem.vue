<template>
  <form class="wrapper">
    <h5>Добавление пользователя</h5>
    <div class="firstRow">
      <div class="name">Имя</div>
      <input v-model="info.name" type="text" class="phone" />
    </div>
    <div class="firstRow">
      <div class="name">Телефон</div>
      <input v-model="info.phone" type="text" class="phone" />
    </div>
    <div class="firstRow">
      <div class="name">Начальник</div>
      <select v-model="info.manager" class="phone">
        <option disabled value></option>
        <option>Олег петров</option>
        <option>Максим Смолов</option>
      </select>
    </div>
    <span @click="$emit('saveInfo', info)" class="btnSave">Сохранить</span>
  </form>
</template>

<script>
export default {
  data() {
    return {
      info: {
        name: "",
        phone: "",
        manager: ""
      }
    };
  }
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: start;
  width: 400px;
  margin-top: 50px;
  border: 1px black solid;
}
.firstRow {
  width: 100%;
  display: flex;
  justify-content: space-between;
}
.name {
  margin-left: 30px;
}
.phone {
  margin-right: 50px;
}
.btnSave {
  background: #e4dfdf;
  text-align: center;
  width: 30%;
  height: 20px;
  margin: 20px;
  border-radius: 7px;
  border: 1px solid black;
}
</style>
