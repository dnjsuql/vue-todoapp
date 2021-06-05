<template>
  <div class="contents">
    <Add @addItem="addOneItem" />
    <List :propsdata="todoItems" @removeItem="removeOneItem" />
    <Button @clickLogCheck="checking" />
    <NewList :logdata="msg" />
    <CommonButton v-bind:title="t"/>
  </div>
</template>

<script>
import Add from '@/views/components/Add.vue'
import List from '@/views/components/List.vue'
import Button from '@/views/components/Button.vue'
import NewList from '@/views/components/NewList.vue'
import CommonButton from '@/views/components/CommonButton.vue'

export default {
  name: 'contents',
  components: {
    Add,
    List,
    Button,
    NewList,
    CommonButton
  },
  data() {
    return {
      todoItems: [],
      msg: []
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
    checking(item){
      const value = {
        itemz: item
      };
      this.msg.push(value);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.contents {
  padding: 0 20px;
  border: 1px solid #999;
  background-color: #efefef;
  flex: 1;
}
</style>
