<template>
<!-- general wrapper -->
  <div class="wrapper flexBox">
    <div class="name flexBox">{{dataItem.name}}</div>
    <div class="phone flexBox">{{dataItem.phone}}</div>
  </div>
</template>  

<script>
export default {
  props: {
    dataItem: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
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
.name {
  width: 40%;
  padding: 10px;
  border-right: 1px black solid;
}
.phone {
  width: 60%;
  padding: 10px;
}
</style>