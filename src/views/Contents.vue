<template>
  <div class="contents">
    <Add v-on:addItem="addOneItem" />
    <List
      v-bind:propsdata="todoItems"
      v-on:removeItem="removeOneItem"
    />
  </div>
</template>

<script>
import Add from '@/views/components/add.vue'
import List from '@/views/components/list.vue'

export default {
  name: 'contents',
  components: {
    Add,
    List
  },
  data() {
    return {
      todoItems: []
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
          this.todoItems.push(
            JSON.parse(localStorage.getItem(localStorage.key(i)))
          );
        }
      }
    }
  },
  methods: {
    addOneItem(todoItem) {
      var value = {
        item: todoItem,
      };
      localStorage.setItem(todoItem, JSON.stringify(value));
      this.todoItems.push(value);
    },
    removeOneItem(todoItem, index) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.contents {
  padding: 0 20px;
  border: 1px solid #999;
  flex: 1;
}
</style>
