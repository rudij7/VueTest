<template>
  <v-container>
    <v-simple-table>
      <tbody>
        <tr v-for="(item, index) in data" :key="item.id">
          <td>{{ item.id }}</td>
          <td>
            <v-text-field
              v-model="item.value"
              :value="item.value"
              flat
              :disabled="!(disabled == index)"
            ></v-text-field>
          </td>
          <v-btn v-if="disabled != index" v-on:click="edit(index)">Edit</v-btn>
          <v-btn v-if="disabled == index" v-on:click="edit(index)">Save</v-btn>
          &nbsp;&nbsp;&nbsp;<v-btn v-on:click="remove(index)">Delete</v-btn>
        </tr>
      </tbody>
    </v-simple-table>
  </v-container>
</template>

<script>
import items from "./json/tableData7Records.json";

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
