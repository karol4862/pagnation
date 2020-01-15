<template>
  <div class="overflow-auto">
    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      aria-controls="my-table"
    ></b-pagination>

    <p class="mt-3">Current Page: {{ currentPage }}</p>
    <b-table small :items="items" responsive="sm" :per-page="perPage"
      :current-page="currentPage">

      <!-- Optional default data cell scoped slot -->
      <template v-slot:cell()="data">
        <i>
          {{ data.value }}
          <!-- v-if below for object's property-->
          <input
            v-if="data.field.key === 'age'"
            type="number"
            v-model="items[data.item.id - 1][data.field.key]"
          />
        </i>
      </template>
    </b-table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      perPage: 3,
      currentPage: 1,
      items: [
        { id: 1, first_name: 'Fred', age: 30 },
        { id: 2, first_name: 'Wilma', age: 30 },
        { id: 3, first_name: 'Barney', age: 30 },
        { id: 4, first_name: 'Betty', age: 30 },
        { id: 5, first_name: 'Pebbles', age: 30 },
        { id: 6, first_name: 'Bamm Bamm', age: 30 },
        { id: 7, first_name: 'The Great', age: 30 },
        { id: 8, first_name: 'Rockhead', age: 30 },
        { id: 9, first_name: 'Pearl', age: 30 },
      ],
    };
  },
  methods: {
    changeValue(id, key, value) {
      this.items[id - 1][key] = value + 1;
    },
  },
  computed: {
    rows() {
      return this.items.length;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
