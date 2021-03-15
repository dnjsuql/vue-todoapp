<template>
  <ul class="list">
    <li class="list__item"
      v-for="(todoItem, index) in propsdata"
      v-bind:key="todoItem.item"
    >
      <input
        type="checkbox"
        class="list__checkbox"
        v-bind:id="todoItem.item"
      >
      <label
        v-bind:for="todoItem.item"
        class="list__label"
      >
        <p class="list__text">{{ todoItem.item }}</p>
      </label>
      <!-- <span class="list__date">5/26</span> -->
      <button type="button" class="list__delete" @click="removeTodo(todoItem, index)">x</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'list',
  props: ['propsdata'],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit("removeItem", todoItem, index);
    }
  }
}
</script>

<style lang="scss" scoped>
.list {
  margin-top: 10px;
  &__item {
    padding-left: 32px;
    padding-right: 32px;
    width: 100%;
    height: 50px;
    background-color: yellow;
    position: relative;
    & + & {
      margin-top: 10px;
    }
  }
  &__label {
    display: block;
    height: 100%;
  }
  &__text {
    height: 100%;
    font-size: 14px;
    color: #333;
    display: flex;
    align-items: center;
  }
  &__checkbox {
    position: absolute;
    top: 50%;
    left: 8px;
    transform: translateY(-50%);
    margin: 0;
    border: 1px solid #ccc;
    width: 16px;
    height: 16px;
    background-color: #fff;
    appearance: auto;
  }
  &__date {
    position: absolute;
    bottom: 8px;
    right: 8px;
    font-size: 10px;
  }
  &__delete {
    position: absolute;
    top: 8px;
    right: 8px;
    width: 16px;
    height: 16px;
    font-size: 12px;
    background-color: red;
  }
}
</style>
