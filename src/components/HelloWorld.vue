<template>
  <table>
    <tbody>
      <tr v-for="(item, index) in data" :key="item.id">
        <td>{{ item.id }}</td>
        <td>
          <input
            type="text"
            v-model="item.value"
            :disabled="!(disabled == index)"
          />
        </td>
        <td>
          <button
            type="button"
            v-if="disabled != index"
            v-on:click="edit(index)"
          >
            Edit
          </button>
          <button
            type="button"
            v-if="disabled == index"
            v-on:click="edit(index)"
          >
            Save
          </button>
          &nbsp;&nbsp;&nbsp;<button type="button" v-on:click="remove(index)">
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import items from "./json/tableData7Records.json";
import "./helloworld.css";

export default {
  name: "HelloWorld",
  methods: {
    remove: function(index) {
      this.data.splice(index, 1);
    },

    edit: function(index) {
      if (this.disabled == -1) {
        this.disabled = index;
      } else if (this.disabled == index) this.disabled = -1;
    },
  },
  data: () => ({
    disabled: -1,
    data: items,
  }),
};
</script>
