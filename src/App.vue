<template>
  <div>
    <h1>Wardrobe Management System</h1>
    <AddClothing />
    <ClothingList />
  </div>
</template>

<script>
import AddClothing from "./components/AddClothing.vue";
import ClothingList from "./components/ClothingList.vue";

export default {
  components: {
    AddClothing,
    ClothingList,
  },
};
</script>

<style>
h1 {
  text-align: center;
}
</style>
