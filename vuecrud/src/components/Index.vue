<template>
  <div>
      <h1>Items</h1>

      <table class="table table-hover">
          <thead>
              <tr>
                <td>ID</td>
                <td>Item Name</td>
                <td>Item Price</td>
                <td>Actions</td>
              </tr>
          </thead>
          <tbody v-if="items.length > 0">
            <tr v-for="item in items" :key="item._id">
              <td>{{ item._id }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.price }}</td>
              <td>
                <router-link :to="{name: 'Edit', params: { id: item._id }}" class="btn btn-primary btn-sm me-2">Edit</router-link>
                <button class="btn btn-danger btn-sm" v-on:click="deleteItem(item._id)">Delete</button>
              </td>
            </tr>
          </tbody>
          <tbody v-else>
            <tr>
              <td colspan="4">No item found.</td>
            </tr>
          </tbody>
      </table>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data() {
    return {
      items: []
    }
  },
  created: function()
  {
    this.fetchItems();
  },
  methods: {
    fetchItems() {
      let uri = 'http://localhost:3000/items';
      this.axios.get(uri)
        .then((response) => {
          console.log(response.data);
          this.items = response.data
        });
    },

    deleteItem(id)
    {
      if (confirm('Are you sure want to delete?')) {
        let uri = 'http://localhost:3000/items/delete/'+id;
        this.items.splice(id, 1);
        this.axios.post(uri)
          .then((response) => {
            console.log(response.data);
            alert(response.data);
          });
      }
    }
  }
}
</script>

<style>

</style>