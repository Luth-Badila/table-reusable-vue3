<template>
  <div class="app">
    <ReusableTable :columns="tableColumns" :items="tableData">
      <template #button1>
        <button class="button1" @click="addNewItem">
          <Icon icon="material-symbols:add" style="font-size: 20px" />
          <span> Add New Item </span>
        </button>
      </template>

      <template #button2>
        <button class="button2" @click="deleteSelectedItem">
          <Icon icon="material-symbols:delete" style="font-size: 20px" />
          <span> Delete </span>
        </button>
      </template>
      <template #button3>
        <button class="button3" @click="exportData">
          <Icon icon="mingcute:edit-line" style="font-size: 20px" />
          <span> Delete </span>
        </button>
      </template>
      <template #form>
        <form @submit.prevent="submitForm">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="formData.name" />

          <label for="age">Age:</label>
          <input type="number" id="age" v-model="formData.age" />

          <button type="submit">Add Item</button>
        </form>
      </template>
    </ReusableTable>
  </div>
</template>

<script>
import ReusableTable from "./components/table.vue";
import { Icon } from "@iconify/vue";

export default {
  components: {
    ReusableTable,
    Icon,
  },
  data() {
    return {
      tableColumns: [
        { key: "id", label: "ID" },
        { key: "name", label: "Name" },
        { key: "age", label: "Age" },
        { key: "address", label: "Address" },
      ],
      tableData: [
        { id: 1, name: "John Doe" },
        { id: 2, name: "Jane Smith", age: 28 },
      ],
      formData: {
        name: "",
        age: null,
      },
    };
  },
  methods: {
    addNewItem() {
      console.log("New Item");
    },
    deleteSelectedItem() {
      console.log("Delete Data");
    },
    exportData() {
      console.log("See details");
    },
    submitForm() {
      // Implement your logic to add a new item using the form data
      this.tableData.push({
        id: this.tableData.length + 1,
        name: this.formData.name,
        age: this.formData.age,
      });

      // Reset the form data
      this.formData.name = "";
      this.formData.age = null;
    },
  },
};
</script>

<style>
.app {
  font-family: Arial, sans-serif;
  margin: 20px;
}
.button1,
.button2,
.button3 {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
}
</style>
