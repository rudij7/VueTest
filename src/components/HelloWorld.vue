<template>
  <v-container>
    <v-simple-table>
    
      <tbody>
        <tr v-for= "(item, index) in data" :key="item.id">
          <td>{{item.id}}</td>
          <td><v-text-field :value=item.value flat :disabled="disabled"></v-text-field></td>
          <v-btn v-on:click='disabled = !disabled'>Edit</v-btn>
          <v-btn v-on:click="remove(index)">Delete</v-btn>
        </tr>
        
      </tbody>
      
    </v-simple-table> 
  </v-container>
</template>

<script>
import items from './json/items.json'

  export default {
    name: 'HelloWorld',
    
    data: () => ({
      disabled: true,
      methods: {
        remove: function(index) {
          this.data.splice(index, 1);

        }
      },
        data: items         
    }),
  }
</script>
