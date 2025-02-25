<template>
  <div>
    <h2>Wardrobe Items</h2>
    <ul v-if="clothingItems.length">
      <li v-for="item in clothingItems" :key="item.id">
        {{ item.name }} - {{ item.category }} ({{ item.color }})  
        <button @click="deleteItem(item.id)">Delete</button>
      </li>
    </ul>
    <p v-else>No clothing items found.</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      clothingItems: [],
    };
  },
  methods: {
    async fetchClothingItems() {
      try {
        const response = await axios.get("/clothing-items");
        this.clothingItems = response.data;
      } catch (error) {
        console.error("Error fetching clothing items:", error);
      }
    },
    async deleteItem(id) {
      try {
        await axios.delete(`/clothing-items/${id}`);
        this.fetchClothingItems(); // Refresh list
      } catch (error) {
        console.error("Error deleting item:", error);
      }
    },
  },
  mounted() {
    this.fetchClothingItems();
  },
};
</script>

<style>
button {
  margin-left: 10px;
  color: white;
  background: red;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
