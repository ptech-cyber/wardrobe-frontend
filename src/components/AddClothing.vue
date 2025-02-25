<template>
  <div>
    <h2>Add Clothing Item</h2>
    <form @submit.prevent="addClothingItem">
      <input v-model="name" placeholder="Item Name" required />
      <select v-model="category">
        <option value="tops">Tops</option>
        <option value="bottoms">Bottoms</option>
        <option value="shoes">Shoes</option>
      </select>
      <input v-model="color" placeholder="Color" />
      <input v-model="size" placeholder="Size" />
      <button type="submit">Add Item</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      name: "",
      category: "tops",
      color: "",
      size: "",
    };
  },
  methods: {
    async addClothingItem() {
      try {
        await axios.post("/clothing-items", {
          name: this.name,
          category: this.category,
          color: this.color,
          size: this.size,
        });
        alert("Item added!");
        this.name = "";
        this.category = "tops";
        this.color = "";
        this.size = "";
      } catch (error) {
        console.error("Error adding item:", error);
      }
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 200px;
}
button {
  background: green;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
}
</style>
