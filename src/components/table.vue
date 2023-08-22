<template>
  <div class="form">
    <div>
      <slot name="button1"></slot>
    </div>
    <div class="button-right">
      <slot name="button2"></slot>
      <slot name="button3"></slot>
    </div>
  </div>
  <table class="reusable-table">
    <thead>
      <tr>
        <th v-for="column in columns" :key="column.key">{{ column.label }}</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in items" :key="item.id">
        <td v-for="column in columns" :key="column.key">{{ item[column.key] }}</td>
      </tr>
    </tbody>
  </table>
  <div class="form-container">
    <slot name="form"></slot>
  </div>
</template>

<script>
export default {
  props: {
    columns: {
      type: Array,
      required: true,
    },
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.form {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  width: 800px;
}
.button-right {
  display: flex;
  gap: 5px;
}
.reusable-table {
  border-collapse: collapse;
  width: 100%;
}

.reusable-table th,
.reusable-table td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}
</style>
